# Tutorial to Elasticsearch indexation
## Installation requirements

Welcome to the Elasticsearch indexation Tutorial!

**Before running the notebook, you will need to have a local running instance of Elasticsearch**

ES8 installation guidelines (Debian package on Linux):

- Download and install the public signing key:
```shell
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg
```
- Installing from the APT repository:
You may need to install the apt-transport-https package on Debian before proceeding
```shell
sudo apt-get install apt-transport-https
```

Save the repository definition to /etc/apt/sources.list.d/elastic-8.x.list:
```shell
echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-8.x.list
```
You can now install the Elasticsearch Debian package with:
```shell
echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-8.x.list
```
```shell
(sudo apt-get update && )sudo apt-get install elasticsearch
```
<br/>

:warning: **NOTE:** We will use a very basic non authenticated setup

```shell
nano etc/elasticsearch/elasticsearch.yml
```

- Navigate to "Security auto configuration" at the bottom and set `xpack.security.enabled`, `xpack.security.http.ssl` & `xpack.security.transport.ssl` to `false`

- Limit ES memory usage:<br/>
https://www.elastic.co/guide/en/elasticsearch/reference/current/advanced-configuration.html#set-jvm-options
  - Add a line delimited file with a .options extension to /etc/elasticsearch/jvm.options.d with following arguments:<br/>
  Example limiting to 2G:<br/>
  ```
  -Xms2g
  -Xmx2g
  ```

- Start Elasticsearch:
```shell
service start elasticsearch
```
- Control if Elasticsearch is up and running:
  - Check http://localhost:9200/ or
  - Run the below command:
   ```shell
   curl 'localhost:9200/_cat/indices?v'
   ```

- Install the server dependencies:
```
python3 -m venv venv
source venv/bin/activate
pip install -r requirements.txt
```
<br/><br/>

**We can now open the notebooks**
```
jupyter notebook
```

## [Part 1: Intro to Elasticsearch](http://localhost:8888/notebooks/elasticsearch_tutorial.ipynb)

Welcome to the Elasticsearch indexation Tutorial!

By the end of this workshop, you will be able to:

- understand the basics of Elasticsearch
- get a high level understanding of the architecture of Elasticsearch
- perform basic CRUD (Create, Read, Update, and Delete) operations with Elasticsearch


