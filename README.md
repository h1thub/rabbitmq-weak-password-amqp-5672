# RabbitMQ Weak Password AMQP 5672 POC

This Nuclei template detects weak credentials (default username/password) on RabbitMQ's AMQP 5672 port, specifically targeting the **guest/guest** default account. If an attacker is able to connect to the RabbitMQ service with these default credentials, they could gain unauthorized access to the message queue, potentially exposing sensitive data or disrupting services.

## Vulnerability Description

By default, RabbitMQ exposes the **guest** user account with the password **guest** on the AMQP 5672 port. This can pose a significant security risk, especially if the service is exposed to the internet or lacks proper network segmentation and authentication mechanisms.

- **Default Username**: guest
- **Default Password**: guest
- **Vulnerable Port**: 5672 (AMQP)

This POC attempts to authenticate with the default credentials on the AMQP 5672 port and checks for the possibility of unauthorized access.

## How It Works

The template attempts to connect to the RabbitMQ service running on port 5672 using the **guest/guest** credentials. If the connection is successful, it indicates that the RabbitMQ service is vulnerable to unauthorized access via weak/default credentials.

## Usage

To run the template, use the Nuclei tool with the following command:

```bash
nuclei -t rabbitmq-weak-password-amqp-5672.yaml -u ip:5672
