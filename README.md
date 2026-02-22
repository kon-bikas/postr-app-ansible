# Ansible post application docker and k8s deployment

Ansible project used for automating tasks for post-backend project deployment. Used to deploy spring post-backend application, keycloak (with keycloak rabbitmq event spi provider), rabbitmq, minio and postgresql with docker-compose to a remote host (spring-docker) or the deployment of a newer version of the spring application in the kubernetes cluster (spring-k8s.yml).

---

## 📦 Requirements for local machine

- Python >= 3.9
- Ansible
- python3-kubernetes

## 📦 Requirements for remote machine

- Python >= 3.9
- docker and docker-compose

## 🗂️ Project Structure

. \
├── files/ **Jinja2 template files for testing nginx deployment**\
├── group_vars/ **Group variables**\
├── host_vars/ **Host variables** \
├── playbooks/ **Location of all the project playbooks**\
├── hosts.yml **File that let's ansible connect to remote host** \
└── ansible.cfg **ansible config file, specifying inventory and ssh args**

## 🖥 Remote Host Configuration
Make sure that you have an entry in ~/.ssh/config file with the same name as your app server host in hosts.yml file
```bash
Host aws-app-server
        HostName <app-server-ip>
        User <app-server-user>
        Port 22
        IdentityFile <path-to-private-ssh-key>
```

## 🚀 Run The Playbooks
#### Run spring-docker.yml playbook
**❗NOTE:** If docker and docker composed is not present in the remote host, it will run the docker.yml playbook to install them. 

assuming that you are in the root of the project:
```bash
ansible-playbook playbboks/spring-docker.yml
```

#### Run spring-k8s.yml playbook
assuming that you are in the root of the project:
```bash
ansible-playbook playbboks/spring-k8s.yml
```

