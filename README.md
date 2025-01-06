## Lemonade payments 
## Devops Engineer technical assessment - answers
### Presented by: Zack Mwangi [ zackmwangi@gmail.com ]
### Date: Jan 06, 2025

---

### Section 1: General Technical knowledge
#### Q1: What are the key security concerns when it comes to DevOps?
> ##### Ans:
> 
 
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

#### Q9: A Postgres query is running slower than expected. Explain your approach to troubleshooting it.
##### Ans:

#### Q10: Write a Dockerfile to containerize a Laravel application.
##### Ans:

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

