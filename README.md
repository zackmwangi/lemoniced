## Lemonade payments 
## Devops Engineer - Technical Assessment - submission
### Submitted by: Zack Mwangi [ zackmwangi@gmail.com ]
### Date: Jan 07, 2025

---

## Section 1: General Technical knowledge
#### Q1: What are the key security concerns when it comes to DevOps?
> ##### Ans:
> DevOps as a philosophy aims to improve the delivery cycle of software products through integration and automation 
of software development and delivery workflows. It is an important part of modern product development culture but inevitably comes with several security concerns including:

**Secrets management** - Secrets include passwords,keys and other sensitive credentials that should always remain controlled to prevent leakage and systems compromise.
###### Considerations:
- Use of vault services(Hashicorp Vault as an example) to reduce exposure of secrets when bundled with application code.
- Separation of concerns by ensuring software that consumes secrets is not bundled together with secrets themselves.
- Dynamic secret generation and rotation -  to ensure secrets are not perpetually reused especially in sensitive environments such as the Lemonade infrastructure.

**Infrastructure-as-code validation** - DevOps attempts to define the entire infrastructure as code and this means any vulnerabilities can lead to the compromise of entire systems.
###### Considerations:
- Usage of scanning tools (such as Terrascan) to mitigate release of code with known vulnerabilities.
- Regular security audits of infrastructure templates, which should also be standardized where possible.

**Supply chain attacks** - The concern here arises from third party libraries and other dependencies that are usually imported into build processes.
###### Considerations: 
- Software composition analysis and scanning codebases to identify and remediate against known vulnerabilities in imported dependencies.
- Enforce the usase of well tested and validated third-party libraries throughout the development process and moreso in production environments.

**Insecure code release** - increased velocity and frequency of release means that untested software can get to production much faster.
###### Considerations: 
- Secure coding practices, including code review need to be part of the development culture.
- Automated (and manual) testing and analysis throughout the development and release cycle.

**Compliance risks** - Meeting and adhering to regulatory frameworks can result in significant penalties especially in heavily regulated environments and industries such as Fintech.
###### Considerations: 
- Implementation of automated compliance checks in the CI/CD workflows to catch potential policy violations early.

**Identity and access management** - Proper access control to infrastructure repositories is important to prevent unauthorized actions on systems.
###### Considerations:
- The principle of least privilige should be part of access control policies.
- Regular audit of access rights and supporting sub-processes need to be implemented to prevent unauthorized access especially when team members change roles or exit the company.

**Container security** - This is related to supply chain attack but am highling it in light of increased packaging of software as containers, such as with Docker and Kubernetes.
###### Considerations:
- Restricted access to container image repositories whether self-hosted or on cloud provider container registries.
- Regular update of base images used in build processes, which should also be minified to reduce attack footprint.
- Regular scanning of base images to mitigate know vulnerabilities and improve runtime software security.
 
#### Q2: How do you design a self-healing distributed service?
##### Ans:
>A self-healing service is one which maintains a high level of availability and resilience against failure while gracefully recovering from 
any failures with minimal deviation from the stipulated level of performance.

A design towards achieving these goals would entail:

**Implementing health checks** - A regular healthcheck on the service means that an observer system can detect issues and implement swift corrective measures such as restarts.
###### Considerations:
- Implement liveness and readiness probe endpoints in all deployed micro-services and use platform or orchestrator probes to continuously monitor service health.

**Using replicated instances** - This ensures more than one instance of the service is available to respond to requests.
###### Considerations:
- Use of automated orchestration systems such as Kubernetes replica sets to ensure the minimum number of replicas is always running.
- Each replica should be deployed in a different availability zone to further reduce chances of localized mass failure.

**Load balancing** - Distributing traffic improves service availbility in case of hosting node failure.
###### Considerations: 
- Use of load-aware distribution policies in case of high traffic and unforeseen traffic spikes.
- Design of stateless services that share distributed state to ensure smooth customer experience accross requests even in times of node failures.

**Auto-scaling** - Dynamically increasing service capacity in times of high demand is recommended to reduce service degradation or failure.
###### Considerations:
- Use of orchestration tools that support both horizontal (and potentially vertical) auto-scaling of service instances.

**Rolling updates and rollbacks** - These are aimed at ensuring high service availability amidst continuous integrations and constant update/redeployment.
###### Considerations: 
- Implement a deployment strategy such as canary-update for zero-downtime updates.
- Implement a roll-back strategy, monitoring any new service releases for errors and restoring to the last-known healthy version quickly to reduce downtime.

**Monitoring and logging** - Detecting issues early is important especially when services may appear to run normally but produce incorrect outputs.
###### Considerations:
- Monitoring and alerting for unusual patterns in logs to catch impending failures besides the usual known error states.

Additionally I would implement circuit-breaker logic to guard against cascading failures, as well as retry mechanisms to restart/retry failing instances (with a back-off factor).

#### Q3: Describe a centralized logging solution and *how* you can implement logging for a microservice architecture
##### Ans:
>At a high level, the centralized logging solution entails individual micro-services sending logs to a central collector, which would then forward them to a bulk-storage solution and also expose them through a visualization tool. Some processing may also be done by the collector/aggregator logic to ensure standardized log structures and formats for search and analysis.

Implementation of centralized logging for micro-services would involve:
 
 - **Collection of logs** from individual hosts, containers and services using a client such as Fluentd
 - **Establish a Logging format/structure** - Establishing a consistent format to ensure consistent parsing, correlation and analysis.
 - **Aggregation** of the logs onto a central collector, backed by a storage solution
 - **Log processing/analysis** by extracting features from the logs. Optionally a streaming service such as Kafka/Redpanda may be implemented for real-time processing.
 - **Indexing and enrichment** for easier searching and correlation is important to enable quick tracing or root causes of failure across service boundaries.
 - **Visualization tooling** such as Kibana would also be attached to provide quick insight into logs during troubleshooting. 
 - **Alerting thresholds** and rules are also necessary here to ensure error states are spotted, reported and investigated as soon as they are triggered to minimize downtime and negative impact on service availability.
 - **Storage/rotation and retention policies** - management of log data and retention for stipulated durations is important for performance and compliance. A tiered storage solution would be ideal to balance cost and quick accessibility. Older copies may be stored in cheaper but slower volumes while faster and highly accessible/real-time solutions are used for newer log files that are highly likely to be required in case of failure.

 Specific tooling used for the collection, aggregation, search, alerting and visualization may vary, form the older Elasticsearch, Logstash, Kibana(ELK) stack, to newer and improved tools and cloud-native solutions.

 Other considerations include ensuring secure access to logs to prevent tampering especially in cases of systems compromise and criminal incidences. Some food for thought arises here if we also consider build-vs-buy in comparison to cloud-native options such as Amazon CloudWatch, GCP Cloud logging, etc in cases where the infrastructure is built on such providers.


#### Q4: What are some of the reasons for choosing Terraform for DevOps?
##### Ans:

#### Q5: How would you design and implement a secure CI/CD architecture for microservice deployment using GitOps? Take a scenario of 20 microservices developed using different languages and deploying to an orchestrated environment like Kubernetes. (You can add a low-level architectural diagram)
##### Ans:

#### Q6: You notice React Native builds are failing intermittently. What’s your debugging process?
##### Ans:

---

## Section 2: Coding Challenge
#### Q7: Write Prometheus exporter in Python/Golang that connects to specified RabbitMQ HTTP API (it's in the management plugin) and periodically reads the following information about all queues in all vhosts:

> * messages (total count of messages)
> * messages_ready
> * messages_unacknowledged

> It should then export 3 new metrics:
> * rabbitmq_individual_queue_messages{host,vhost,name}
> * rabbitmq_individual_queue_messages_ready{host,vhost,name}
> * rabbitmq_individual_queue_messages_unacknowledged{host,vhost,name}

where the host is RabbitMQ hostname, vhost is RabbitMQ vhost and name is name of the queue.
It should use **RABBITMQ_HOST , RABBITMQ_USER, and RABBITMQ_PASSWORD** environment variables to run multiple deployments of this and just change the env in them.

##### Ans:

#### Q8: Write a script to restart the Laravel backend service if CPU usage exceeds 80%
##### Ans:
> Solution in question_8 folder [>> click here to go to solution folder <<](./question_8/README.md)

#### Q9: A Postgres query is running slower than expected. Explain your approach to troubleshooting it.
##### Ans:

#### Q10: Write a Dockerfile to containerize a Laravel application.
##### Ans:
> Solution in question_10 folder [>> click here to go to solution folder <<](./question_10/README.md)

---

## Section 3: Monitoring and Troubleshooting
#### Q11: How would you set up monitoring for the React Native mobile app’s API endpoints?
##### Ans:

#### Q12: Explain how you would debug high latency in the Node.js microservices.
##### Ans:

---

## Section 4: Behavioral
#### Q13: Describe a time you improved the performance of an infrastructure system. What challenges did you face?
##### Ans:

#### Q14: How do you prioritize tasks when multiple urgent issues arise?
##### Ans:

