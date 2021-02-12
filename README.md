**Compose all microservices belonging to reciter environment**

The ReCiter environment consists of a couple of services working together to disambiguate authors and their publications. To run these services together and on your local machine, use the docker-compose.yml or docker-compose-w-scopus.yml files.

**Prerequisite**:  group "docker" needs write permissions on folder ReCiter-Local/dynamodblocal

The services run on the following ports:
- ReCiter: 5000
- ReCiter-PubMed-Retrieval-Tool: 5002
- ReCiter-Scopus-Retrieval-Tool: 5001

and can be reached via their respective swagger-ui: http://localhost:<port>/swagger-ui/


**Note**
ReCiter is not downloaded from the main project, but from a fork.
It uses the branch "dynamodb_local" and the only change is in file DynamoDbConfig.java 
to use  "http://dynamo" as URL for the local dynamodb service instead of "http://docker.for.mac.host.internal". 
This uses the network docker-compose is setting up instead of relying on OS-dependent fix.