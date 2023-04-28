# Web App for Open Search Scaling Manager

### Overview

We have introduced REST API that allows for more flexible and scalable communication and easy integration for OpenSearch Scaling Manager. 

### Approach

- The older approach required manual execution of Ansible commands via CLI, whereas the new REST API enables the creation of endpoints that can automate and streamline these tasks.
- The adoption of REST API eliminates the need for manual intervention and enables the OpenSearch Scaling Manager to operate more efficiently.

### Architecture

The design includes following components

- Upload and Unzip
- Populate Inventory
- Install
- Start
- Stop
- Update
- Status
- Update PEM

#### Upload and Unzip

- The latest version of artifacts of OSM will be Uploaded.
- The latest build of Scaling Manager artifacts will be available in the OSM GitHub page.
- The code will Unzip the artifacts and store in folder.
- Artifacts is the zip file containing the following components
  1. install_scaling_manager.yaml.
  2. GNUmakefile.
  3. scaling_manager.tar.gz.

#### Populate Inventory

- The master node ip , OpenSearch user and OpenSearch password  is provided.
- Based on the master node details provided, the other details of data nodes of the cluster are populated into inventory.yaml.

#### Install 

- Based on the details provided in ansible file this  API will install all the dependencies in the data node mentioned in inventory file.

#### Start 

- Starts the scaling manager through which metrics will be collected and perform task(Scaleup or Scaledown) accordingly.

#### Stop 

- Stops the Scaling Manager.

#### Update config

- Update the scaling manager with the latest changes done to config file.

#### Update PEM 

- Update done to the PEM will be replaced with older version of PEM.

#### Status 

- Provides the current status of the nodes.
- It will also provides the description of the errors while performing the tasks. 



### API'S

We have the following API's for the Open search Scaling Manager



| Path           | Description                                                 | Method |                       Path Parameters                        | Request Body | Response                |
| -------------- | ----------------------------------------------------------- | ------ | :----------------------------------------------------------: | ------------ | ----------------------- |
| /upload        | Takes the artifacts and unzip it into the specified folder. | POST   |                             NONE                             | File         | {"message"type :string} |
| /populate      | Populates the inventory file.                               | POST   | master ip : string        os_user : string          os_password : string | NONE         | {"message"type :string} |
| /install       | Installs the Scaling Manager .                              | GET    |                             NONE                             | NONE         | {"message"type :string} |
| /start         | Start the Scaling Manager .                                 | GET    |                             NONE                             | NONE         | {"message"type :string} |
| /stop          | Stop the Scaling Manager                                    | GET    |                             NONE                             | NONE         | {"message"type :string} |
| /status        | Returns the status of the nodes.                            | GET    |                             NONE                             | NONE         | {"message"type :string} |
| /update_config | Updates the configuration                                   | GET    |                             NONE                             | NONE         | {"message"type :string} |
| /update_pem    | Updates the PEM file.                                       | GET    |                             NONE                             | NONE         | {"message"type :string} |
| /uninstall     | Uninstall the scaling manager                               | GET    |                             NONE                             | NONE         | {"message"type :string} |



### OSM UI
For more information on UI Please follow [UI Documentation](https://github.com/Akhil-Nair-ML/OSM-WEBAPP/opensearch-scaling-manager-ui/README.md)