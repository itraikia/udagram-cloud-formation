# Solution Diagram
The Udagram solution diagram is available at /diagram
ther's an image exposing the diagram and the .drawio file which can be open in https://app.diagrams.net/

The diagram expose the solution architecture including network and resources.


# CloudFormation Networking Resources
Cloud formation networking resouces are exposed in network.yml file, parameters are exposed in network-parameters.json


# CloudFormation Apllication Resources
Cloud formation application resouces are exposed in udagram.yml file, parameters are exposed in udagram-parameters.json


# Scripts
there are 3 scripts :
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
3. delete.sh : then you can remove the cloudformation infrastructure by executing the scripts under.
###
```sh scripts/delete.sh udagram-network-stack```
###
```sh scripts/delete.sh udagram-application-stack```
###
IMPORTANT : the stack-name should be unique
