# Dkron

This is docker compose for running Dkron with zookeeper

## Documentation

http://dkron.io/docs/getting-started/

### State Keeper Options

* etcd
* Consul
* ZooKeeper



### REST API

http://dkron.io/docs/api

#### Job schema

http://dkron.io/docs/api/#job

#### Sample Request to create Job

##### Request

POST /v1/jobs

```
{"name":"shelljobjava","schedule":"* * * * *","command":"java -jar /jobs/target/sample-scheduled-app.jar","shell":true}
```

##### Response

```
{
  "name": "shelljobjava",
  "schedule": "* * * * *",
  "shell": true,
  "command": "java -jar /jobs/target/sample-scheduled-app.jar",
  "owner": "",
  "owner_email": "",
  "success_count": 0,
  "error_count": 0,
  "last_success": "0001-01-01T00:00:00Z",
  "last_error": "0001-01-01T00:00:00Z",
  "disabled": false,
  "tags": null,
  "retries": 0,
  "dependent_jobs": null,
  "parent_job": "",
  "processors": null,
  "concurrency": "allow"
}
```




## Highlights

### Pros

1. Supports Shell
2. Supports dependent jobs (with parent/child concept)
3. Fault tolerant without any Load Balancer unlike Rundeck
4. Good documentation
5. REST API Documentation is verbose
6. Retries configuration available via API
7. Light weight component


### Cons
1. UI is for deleting job and seeing job  history and stats. Option of Adding Job via UI seems to be missing
2. Cannot create/edit/delete job with UI
3. Cron tab expression over Chronos support of ISO8601-based schedules
4. Unlike ChronOS(which used MESOS cluster) integration with Spark workers does not appear to be available
