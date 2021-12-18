# Setting up Elasticsearch Cluster

## _The Last Markdown Editor, Ever_

this is the LAB guide for the Article [How to setup Elasticsearch Cluster](https://thenetmechanic.com/how-to-setup-elasticsearch-cluster/)

## Prerequisite

- [VirtualBox](https://www.virtualbox.org/)
- [Vagrant](https://www.vagrantup.com/)

## Lab Setup

| Hostname | IP Address    | OS      |
| -------- | ------------- | ------- |
| master01 | 192.168.10.12 | Centos7 |
| data01   | 192.168.10.13 | Centos7 |
| data02   | 192.168.10.14 | Centos7 |

## Starting the Lab

```sh
git clone https://github.com/samirsomer/elk-cluster-lab
cd elk-cluster-lab
vagrant up
```

## Master Node Configuration

Elasticsearch Installation & Configuration

```sh
yum update -y

# update the hosts files
cp /vagrant/configuration/common/hosts  /etc/hosts

# download and install Elasticsearch
rpm --import https://artifacts.elastic.co/GPG-KEY-elasticsearch
curl -O https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.6.0-x86_64.rpm
rpm --install elasticsearch-7.6.0-x86_64.rpm
rm -f elasticsearch-7.6.0-x86_64.rpm

cp /vagrant/configuration/master01/elasticsearch.yml /etc/elasticsearch/elasticsearch.yml

firewall-cmd --add-port=9200/tcp --add-port=9300/tcp

systemctl enable elasticsearch
systemctl start elasticsearch
```

Kibana Installation & Configuration

```sh
sudo curl -O https://artifacts.elastic.co/downloads/kibana/kibana-7.6.0-x86_64.rpm
sudo rpm --install kibana-7.6.0-x86_64.rpm
sudo rm -f kibana-7.6.0-x86_64.rpm

cp /vagrant/configuration/master01/kibana.yml /etc/kibana/kibana.yml

sudo systemctl enable kibana
sudo systemctl start kibana
```

## Data01 Node Configuration

Elasticsearch Installation & Configuration

```sh
yum update -y

# update the hosts files
cp /vagrant/configuration/common/hosts  /etc/hosts

# download and install Elasticsearch
rpm --import https://artifacts.elastic.co/GPG-KEY-elasticsearch
curl -O https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.6.0-x86_64.rpm
rpm --install elasticsearch-7.6.0-x86_64.rpm
rm -f elasticsearch-7.6.0-x86_64.rpm

cp /vagrant/configuration/data01/elasticsearch.yml /etc/elasticsearch/elasticsearch.yml

firewall-cmd --add-port=9200/tcp --add-port=9300/tcp

systemctl enable elasticsearch
systemctl start elasticsearch
```

## Data02 Node Configuration

Elasticsearch Installation & Configuration

```sh
yum update -y

# update the hosts files
cp /vagrant/configuration/common/hosts  /etc/hosts

# download and install Elasticsearch
rpm --import https://artifacts.elastic.co/GPG-KEY-elasticsearch
curl -O https://artifacts.elastic.co/downloads/elasticsearch/elasticsearch-7.6.0-x86_64.rpm
rpm --install elasticsearch-7.6.0-x86_64.rpm
rm -f elasticsearch-7.6.0-x86_64.rpm

cp /vagrant/configuration/data02/elasticsearch.yml /etc/elasticsearch/elasticsearch.yml

firewall-cmd --add-port=9200/tcp --add-port=9300/tcp

systemctl enable elasticsearch
systemctl start elasticsearch
```
