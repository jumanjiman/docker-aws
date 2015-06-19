AWS CLI
=======

[![](https://badge.imagelayers.io/jumanjiman/aws.svg)](https://imagelayers.io/?images=jumanjiman/aws:latest 'View image size and layers')&nbsp;
[![Circle CI](https://circleci.com/gh/jumanjihouse/docker-aws.png?circle-token=5303a3a083c3d19463bbd1b08937b24b3417d70e)](https://circleci.com/gh/jumanjihouse/docker-aws/tree/master 'View CI builds')

Project: [https://github.com/jumanjihouse/docker-aws]
(https://github.com/jumanjihouse/docker-aws)

Docker image: [https://registry.hub.docker.com/u/jumanjiman/aws/]
(https://registry.hub.docker.com/u/jumanjiman/aws/)


About
-----

This git repo provides [AWS CLI](http://aws.amazon.com/cli/)
from [PIP](https://pypi.python.org/pypi/awscli) in a Docker container.


How-to
------

### Build and test

    make all
    make test


### Pull an already-built image

    docker pull jumanjiman/aws


### Run

Interactively:

    docker run --rm -it \
    -e AWS_ACCESS_KEY_ID=<snip> \
    -e AWS_SECRET_ACCESS_KEY=<snip> \
    -e AWS_DEFAULT_REGION=us-west-2  \
    --read-only \
    --cap-drop all \
    jumanjiman/aws ec2 describe-instances

As a simplification, add this to your `~/.bashrc`:

    # Use a remote docker host.
    export DOCKER_HOST='tcp://192.168.254.162:2375'

    # Put your keys in the redacted values.
    function aws {
      docker run --rm -it \
      -e AWS_ACCESS_KEY_ID=redacted \
      -e AWS_SECRET_ACCESS_KEY=redacted \
      -e AWS_DEFAULT_REGION=us-west-2 \
      jumanjiman/aws $@
    }

Then `source ~/.bashrc` and simply run `aws <your args>`.