# Chronos with Mesos

This is docker compose config inspired by [blog post by Sebastien Goasguen]
(http://sebgoa.blogspot.com/2015/03/1-command-to-mesos-with-docker-compose.html).

It uses official images from mesosphere and host networking to enable
interactions with tasks over real network. It also enables docker containerizer.
No state is persisted between runs so feel free to start over if you
screwed cluster state or something.

## Versions

* Mesos 1.2.0
* Chronos 2.4.0


Note that you need `docker-compose` 1.6.0 or newer:

* https://github.com/docker/compose

## Compatibility

This project should work out of the box with docker machine. It requires
host networking to work, so docker for mac won't work.

Some differences between Docker for Mac and Dcoker ToolBox
(https://docs.docker.com/docker-for-mac/docker-toolbox/#docker-toolbox-and-docker-for-mac-coexistence)

If you have docker built dynamically, which is the case on most distros,
you should download and bind-mount statically linked docker client:

```
curl -sL https://get.docker.com/builds/Linux/x86_64/docker-1.11.1.tgz | \
  tar xv --strip-components 1 -C /usr/local/bin
```

This downloads docker 1.11.1 and installs binaries into `/usr/local/bin`.

## Usage

You have to specify `DOCKER_IP` env variable in order to make Mesos work
properly. The default value is `127.0.0.1` and it should work if you have
Docker daemon running locally.

If you use `docker-machine` you can do the following, assuming `dev` is your
machine's name:

```
export DOCKER_IP=$(docker-machine ip dev)
```

Run your cluster in the background (equivalent to `docker-compose up -d`):


That's it, use the following URLs:

* http://$DOCKER_IP:5050/ for Mesos master UI
* http://$DOCKER_IP:5051/ for the first Mesos slave UI
* http://$DOCKER_IP:5052/ for the second Mesos slave UI
* http://$DOCKER_IP:8080/ for Chronos UI

If you want to run your cluster in foreground to see logs and be able to stop
it with Ctrl+C, use the following (equivalent to `docker-compose up`):

## Overall Architecture ##

![Diagram](/projects/PSLL/repos/poc/browse/chronos/documents/Chronos.jpg)

## Chronos REST API

https://mesos.github.io/chronos/docs/api.html#leaders


## Highlights

### Pros

1. Supports Shell
2. Support docker commands (example:- docker run <imageName>) (Can be used for CICD pipeline since docker images can be pushed)
3. Supports dependent jobs (with parent/child concept)
4. Can create/edit/delete job with UI
5. Supports Casandra for job history
6. Fault tolerant without any Load Balancer unlike Rundeck
7. Good documentation and active contributions from Air Bnb
8. REST API Documentation is verbose
9. ISO8601-based schedules
10. Retries configuration available via API
11. Notification


### Cons
1. UI is not for job history(Cassandra table is available though)
2. Overhead of Mesos Cluster





