# Running tasks via API:

## Pre-reqs:

A token needs to be generated.

```
curl -k -X POST -H 'Content-Type: application/json' \
 -d '{"login": "admin",
      "password": "puppetlabs",
      "lifetime": "2y"}' \
https://master.inf.puppet.vm:4433/rbac-api/v1/auth/token
```

## Example:

## Start the job:

```
curl -k -X POST 'https://master.inf.puppet.vm:8143/orchestrator/v1/command/task' \
  --data '{ "environment" : "development",
            "task" : "service",
            "params" : {
              "action" : "status",
              "name" : "puppet"
            },
            "scope" : {
              "nodes" : ["simon.anderson-awskit-linux-1"]
            }
          }' \
  -H 'X-Authentication:0S-bII27iwaNApf6G0iDVx8znVlc97SF0Ie9VxqY9p1Q' \
  -H 'Content-Type: application/json'
```

## Start the job, but only return the job number:

```
curl -k -X POST 'https://master.inf.puppet.vm:8143/orchestrator/v1/command/task' \
  --data '{ "environment" : "development",
            "task" : "service",
            "params" : {
              "action" : "status",
              "name" : "puppet"
            },
            "scope" : {
              "nodes" : ["simon.anderson-awskit-linux-1"]
            }
          }' \
  -H 'X-Authentication:0S-bII27iwaNApf6G0iDVx8znVlc97SF0Ie9VxqY9p1Q' \
  -H 'Content-Type: application/json' | jq '.job.name' | tr -d \"
```

## Get the job's status:
```
curl -k -X GET 'https://master.inf.puppet.vm:8143/orchestrator/v1/jobs/7' \
  -H 'X-Authentication:0S-bII27iwaNApf6G0iDVx8znVlc97SF0Ie9VxqY9p1Q' \
  -H 'Content-Type: application/json'
```

## Get the job report:

```
curl -k -X GET 'https://master.inf.puppet.vm:8143/orchestrator/v1/jobs/7/report' \
  -H 'X-Authentication:0S-bII27iwaNApf6G0iDVx8znVlc97SF0Ie9VxqY9p1Q' \
  -H 'Content-Type: application/json'
```

## Get the job events:
```
curl -k -X GET 'https://master.inf.puppet.vm:8143/orchestrator/v1/jobs/7/events' \
  -H 'X-Authentication:0S-bII27iwaNApf6G0iDVx8znVlc97SF0Ie9VxqY9p1Q' \
  -H 'Content-Type: application/json'
```

## Get the job nodes:
```
curl -k -X GET 'https://master.inf.puppet.vm:8143/orchestrator/v1/jobs/11/nodes' \
  -H 'X-Authentication:0S-bII27iwaNApf6G0iDVx8znVlc97SF0Ie9VxqY9p1Q' \
  -H 'Content-Type: application/json'
```
## Get the job results:
```
  curl -k -X GET 'https://master.inf.puppet.vm:8143/orchestrator/v1/jobs/12/nodes' \
    -H 'X-Authentication:0S-bII27iwaNApf6G0iDVx8znVlc97SF0Ie9VxqY9p1Q' \
    -H 'Content-Type: application/json' | jq '. | {result: .items[].result}'
```
## Scripted example:

```
#!/bin/bash
job_number=$(curl -k -X POST 'https://master.inf.puppet.vm:8143/orchestrator/v1/command/task' \
  --data '{ "environment" : "development",
            "task" : "service",
            "params" : {
              "action" : "status",
              "name" : "puppet"
            },
            "scope" : {
              "nodes" : ["simon.anderson-awskit-linux-1"]
            }
          }' \
  -H 'X-Authentication:0S-bII27iwaNApf6G0iDVx8znVlc97SF0Ie9VxqY9p1Q' \
  -H 'Content-Type: application/json' | jq '.job.name' | tr -d \")

sleep 10

echo "Job number: $job_number"

  curl -k -X GET "https://master.inf.puppet.vm:8143/orchestrator/v1/jobs/$job_number/nodes" \
    -H 'X-Authentication:0S-bII27iwaNApf6G0iDVx8znVlc97SF0Ie9VxqY9p1Q' \
    -H 'Content-Type: application/json' | jq '. | {result: .items[].result}'
```
