# RunDeck

This is docker compose for running Rundeck with mysql.
Rundeck is an open source automation service with a web console, command line tools and a WebAPI.
It lets you easily run automation tasks across a set of nodes.

## Documentation

http://rundeck.org/

### State Keeper Options

RDBMS(MySQL)



### REST API

http://rundeck.org/docs/api/index.html




## Highlights

### Pros (API/UI has tons of features)

1. UI has extensive functionality (including creating workflow)
2. Job definition can be uploaded via UI
3. Notifications options available via UI
4. Seems good fit for CI/CD pipeline
5. Log Output is avilable in UI
6. Good documentation
7. Retries configuration available via UI/API



### Cons
1. Fault tolerant is not automatic like Dkron/Chronos(which uses Zookeeper to addisgn leader). Achieved by Load balancer.
   (http://rundeck.org/docs/administration/scaling-rundeck.html)
2.  As per documents “The Rundeck project is in its early stages for building a complete HA and clustering solution.
    We are identifying HA and Clustering requirements and adding them to our roadmap.
    If these features are important to you we encourage you to vote on them or comment!”
    (https://groups.google.com/forum/#!topic/rundeck-discuss/A_Q3yeryKI8)
3. For normal applications which are looking for just scheduling needs this solution appears to be heavy
4. Unlike ChronOS(which used MESOS cluster) integration with Spark workers does not appear to be available
5. Cron tab expression over Chronos support of ISO8601-based schedules


