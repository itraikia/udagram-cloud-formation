# Solution Diagram
The Udagram solution diagram is available at /diagram
ther's an image exposing the diagram and the .drawio file which can be open in https://app.diagrams.net/

The diagram expose the solution architecture including network and resources.


# CloudFormation Networking Resources
Cloud formation networking resouces are exposed in network.yml file, parameters are exposed in network-parameters.json

# CloudFormation Static Resources
Cloud formation static resouces are exposed in static.yml file, parameters are exposed in static-parameters.json


# CloudFormation Apllication Resources
Cloud formation application resouces are exposed in udagram.yml file, parameters are exposed in udagram-parameters.json


# Scripts
there are 4 scripts :
###
```sh scripts/create.sh <stack-name> <stack-template.yml> <stack-template-params.json>```
###
```sh scripts/update.sh <stack-name> <stack-template.yml> <stack-template-params.json>```
###
```sh scripts/delete.sh <stack-name>```
###
1. create.sh : script for create the cloud formation infrastructure, please begin by cloudformation networking resources, then the cloud formation application resources following this order under (Receiving the StackId response significate the success of operations, you should then go to AWS CloudFormation console to see if ther's eventual Rollback and can see the Events for more logs).
###
```sh scripts/create.sh udagram-network-stack network/network.yml network/network-parameters.json```
###
```sh scripts/create.sh static-application-stack static/static.yml static/static-parameters.json```
###
```sh scripts/create.sh udagram-application-stack application/udagram.yml application/udagram-parameters.json```
###
2. update.sh : if you change something in the two CloudFormation templates you can update the stack, using the scripts under (Receiving the StackId response significate the success of operations, you should then go to AWS CloudFormation console to see if ther's eventual Rollback and can see the Events for more logs).
###
```sh scripts/update.sh <stack-name> <stack-template.yml> <stack-template-params.json>```
###
```sh scripts/update.sh udagram-network-stack network/network.yml network/network-parameters.json```
###
```sh scripts/update.sh udagram-application-stack application/udagram.yml application/udagram-parameters.json```
###
###
```sh scripts/update.sh udagram-static-stack application/static.yml application/static-parameters.json```
###
3. delete.sh : then you can remove the cloudformation infrastructure by executing the scripts under.
###
```sh scripts/delete.sh udagram-network-stack```
###
```sh scripts/delete.sh udagram-application-stack```
###
4. deploy.sh : this script is dedicated to deploy the file index.html in the static resource (s3 bucket).
###
```sh scripts/deploy.sh <local-file-path> <resource-name>```
###
```sh scripts/deploy.sh server-content/index.html stagging-s3-bucket-1```
###
IMPORTANT : 
1. the stack-name should be unique
2. the order is important to follow, create first the network infrastructre then the static infrastructure and in last the application infrastructure.
