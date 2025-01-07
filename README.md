## Lemonade payments 
## Devops Engineer - Technical Assessment - submission
### Submitted by: Zack Mwangi [ zackmwangi@gmail.com ]
### Date: Jan 07, 2025

---

### Section 1: General Technical knowledge
#### Q1: What are the key security concerns when it comes to DevOps?
> ##### Ans:
> DevOps as a philosophy aims to improve the delivery cycle of software products through integration and automation 
of software development and delivery workflows. This also inevitably comes with several concerns including:

**Secrets management** - Secrets include passwords,keys and other sensitive credentials that should always remain controlled to prevent leakage and systems compromise.
###### Considerations:
- Use of vault services(Hashicorp Vault as an example) to reduce exposure of secrets as part of normal code
- Separation of concerns by ensuring software that consumes secrets is not bundled together with secrets themselves
- Dynamic secret generation and rotation -  to ensure secrets are not perpetually reused especially in sensitive environments such as the Lemonade infrastructure.

**Infrastructure-as-code validation** - DevOps attempts to define the entire infrastructure as code and this means any vulnerabilities can lead to the compromise of entire systems.
###### Considerations:
- Usage of scanning tools such as(Such as Terrascan) to mitigate release of code with known vulnerabilities.
- Regular security audits of templates (which should also be standardized where possible) would also be necessary.

**Supply chain attacks** - The concern here arises from third party libraries and other dependencies that are usually imported into build processes.
###### Considerations: 
- Software composition analysis and scans to identify and remediate against known vulnerabilities.
- Enforce the usase of well tested and validated third-party libraries throughout the development process and moreso in production environments.

**Insecure code release** - increased velocity and frequency of release means that untested software can get to production much faster.
###### Considerations: 
- Secure coding practices including code review need to be part of the development culture.
- Code review, automated (and manual) testing and analysis throughout the development and release cycle.

**Compliance risks** - Meeting and adhering to regulatory frameworks can result in significant penalties especially in heavily regulated environments and industries such as Fintech.
###### Considerations: 
- Implementation where possible of automated compliance checks in the CI/CD workflows to catch potential policy violations early.

**Identity and access management** - Proper access control to infrastructure repositories is important to prevent unauthorized actions on systems.
###### Considerations:
- The principle of least privilige should be part of access control policies.
- Regular audit of access rights and supporting sub-processes need to be implemented to prevent unauthorized access especially when team members change roles or exit the company.

**Container security** - This is related to supply chain attack but am highling it in light of increased packaging of software as containers, such as with Docker and Kubernetes.
###### Considerations:
- Restricted access to container image repositories whether sel-hosted or on a cloud provider repo.
- Regular update of base images which should also be minimal to reduce attack footprint.
- Regular scanning of base images to mitigate know vulnerabilities and improve runtime software security.
 
#### Q2: How do you design a self-healing distributed service?
##### Ans:

#### Q3: Describe a centralized logging solution and *how* you can implement logging for a microservice architecture
##### Ans:

#### Q4: What are some of the reasons for choosing Terraform for DevOps?
##### Ans:

#### Q5: How would you design and implement a secure CI/CD architecture for microservice deployment using GitOps? Take a scenario of 20 microservices developed using different languages and deploying to an orchestrated environment like Kubernetes. (You can add a low-level architectural diagram)
##### Ans:

#### Q6: You notice React Native builds are failing intermittently. What’s your debugging process?
##### Ans:

---

### Section 2: Coding Challenge
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

### Section 3: Monitoring and Troubleshooting
#### Q11: How would you set up monitoring for the React Native mobile app’s API endpoints?
##### Ans:

#### Q12: Explain how you would debug high latency in the Node.js microservices.
##### Ans:

---

### Section 4: Behavioral
#### Q13: Describe a time you improved the performance of an infrastructure system. What challenges did you face?
##### Ans:

#### Q14: How do you prioritize tasks when multiple urgent issues arise?
##### Ans:

