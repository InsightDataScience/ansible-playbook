## Ansible playbook to deploy distributed technologies

## Setup
1. [Setup ansible for your system](http://docs.ansible.com/ansible/intro_installation.html)
2. Create following folders
 
  <pre>
  <b>~$</b> mkdir -p /etc/ansible/hosts
  </pre>
3. Clone this repo
  
  <pre>
  <b>~$</b> git clone https://github.com/InsightDataScience/ansible-playbook.git
  </pre>

  **NOTE:** To use AWS dynamic inventory
4. Copy the `ec2.py` and `ec2.ini` files in this repo to `/etc/ansible/hosts`
5. Update information in `ansible_example.cfg` and move it to `/etc/ansible/ansible.cfg`
6. Export AWS credentials as environment variables
<pre>
export AWS_ACCESS_KEY_ID=<b>XXXXXXXXXXXXXX</b>
export AWS_SECRET_ACCESS_KEY==<b>XXXXXXXXXXXXXX</b>
</pre>

## Playbooks
1. **EC2**
  * **Vars file**: Update `example_ec2_vars.yml` as per your requirement
  * **Launch EC2 instances**:
  
  ```
  ansible-playbook ./ec2.yml --extra-vars "vars_file=./example_vars_file.yml" --tags launch
  ```
  * **Stop EC2 instances**:
  
  ```
  ansible-playbook ./ec2.yml --extra-vars "vars_file=./example_vars_file.yml" --tags stop 
  ```
  * **Start EC2 instances**:
  
  ```
  ansible-playbook ./ec2.yml --extra-vars "vars_file=./example_vars_file.yml" --tags start 
  ```
  * **Terminate EC2 instances**:
  
  ```
  ansible-playbook ./ec2.yml --extra-vars "vars_file=./example_vars_file.yml" --tags terminate
  ```

2. **Zookeeper** 
  * **Install Zookeeper**:
  ```
  ansible-playbook ./zookeeper.yml --extra-vars "zookeeper_tag=<cluster_tag>" --tags install
  ```
  * **Start Zookeeper**:
  ```
  ansible-playbook ./zookeeper.yml --extra-vars "zookeeper_tag=<cluster_tag>" --tags start
  ```
  * **Get info about Zookeeper on the specified cluster**:
  ```
  ansible-playbook ./zookeeper.yml --extra-vars "zookeeper_tag=<cluster_tag>" --tags info
  ```
  * **Stop Zookeeper**:
  ```
  ansible-playbook ./zookeeper.yml --extra-vars "zookeeper_tag=<cluster_tag>" --tags stop 
  ```
  * **Uninstall Zookeeper**:
  ```
  ansible-playbook ./zookeeper.yml --extra-vars "zookeeper_tag=<cluster_tag>" --tags uninstall
  ```

3. **Kafka** 
  * **Install Kafka**:
  ```
  ansible-playbook ./kafka.yml --extra-vars "zookeeper_tag=<cluster_tag> kafka_tag=<cluster_tag>" --tags install
  ```
  * **Start Kafka**:
  ```
  ansible-playbook ./kafka.yml --extra-vars "zookeeper_tag=<cluster_tag> kafka_tag=<cluster_tag>" --tags start
  ```
  * **Get info about Kafka on the specified cluster**:
  ```
  ansible-playbook ./kafka.yml --extra-vars "zookeeper_tag=<cluster_tag> kafka_tag=<cluster_tag>" --tags info
  ```
  * **Stop Kafka**:
  ```
  ansible-playbook ./kafka.yml --extra-vars "zookeeper_tag=<cluster_tag> kafka_tag=<cluster_tag>" --tags stop 
  ```
  * **Uninstall Kafka**:
  ```
  ansible-playbook ./kafka.yml --extra-vars "zookeeper_tag=<cluster_tag> kafka_tag=<cluster_tag>" --tags uninstall
  ```
