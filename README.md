# docker-acha
[![](https://imagelayers.io/badge/leoschweizer/acha:latest.svg)](https://imagelayers.io/?images=leoschweizer/acha:latest)

This is a lightweight image to run [acha](https://github.com/someteam/acha), the Enterprise Git Achievement solution, in Docker.

## Usage
Without further ado, to run it:
```
$ docker run -d -p 80:80 leoschweizer/acha
```

### Custom SSH keys
A custom SSH key for the use with private repositories can be provided by mounting it into the container:
```
$ docker run -d -p 80:80 \
    -v /path/to/id_rsa:/root/.ssh/id_rsa
    -e ACHA_PRIVATE_KEY=/root/.ssh/id_rsa
```

### Known Hosts
`git clone` will fail if the target host is not known. docker-acha ships with a prepopulated `known_hosts` file for common cloud providers like GitHub or BitBucket (see the `known_hosts` file in this repository for details). However, if you want to support your own git server, you probably have to provide a `known_hosts` file which contains the corresponding SSH host key.
```
$ docker run -d -p 80:80 \
    -v /path/to/known_hosts:/root/.ssh/known_hosts
```

## Contributing
Contributions are welcome. If you have an idea for improvement, don't hesitate to open a ticket.
Add a pull-request to the picture for extra karma.
