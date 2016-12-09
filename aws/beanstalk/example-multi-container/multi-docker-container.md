# multi docker container aws beanstalk

have a look at the file `Dockerrun.aws.json` in this folder, it starts three docker containers on one or multiple ec2 instances.

First a nginx webserver with a link to `app-a` and `app-b` so you can define the hostnames `app-a` and `app-b` within your proxy config file for instance.

It'll also pass some environment variables to the docker container and finally starts an python application with the name `application.py`