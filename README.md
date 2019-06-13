[![Build Status](https://travis-ci.com/trydirect/django-restful.svg?branch=master)](https://travis-ci.com/trydirect/django-restful)
![Docker Stars](https://img.shields.io/docker/stars/trydirect/django-restful.svg)
![Docker Pulls](https://img.shields.io/docker/pulls/trydirect/django-restful.svg)
![Docker Automated](https://img.shields.io/docker/cloud/automated/trydirect/django-restful.svg)
![Docker Build](https://img.shields.io/docker/cloud/build/trydirect/django-restful.svg)
[![Gitter chat](https://badges.gitter.im/trydirect/community.png)](https://gitter.im/try-direct/community)
	
# Django Restful API template

Django Restful API backend template - project generator/development environment.
Can be used by Python developers for quick start on building Restful API's using Django framework and django-rest-framework.
This project is aimed to include most useful tools like RabbitMQ, Redis, Elasticsearch, Kibana, Apidoc 
This project allows you to setup development environment with a single docker-compose command


## Stack includes

* RabbitMQ 
* Redis 
* Elasticsearch
* Logstash
* PostgreSQL
* Nginx
* Supervisord
* Kibana
* Apidoc

Python libraries included:
* django-rest-framework 
* uwsgi
* psycopg2 


## Installation
1. Clone this project into your work directory:
```sh
$ git clone "https://github.com/trydirect/django-restful.git"
```

2. Bring up services with docker-compose:
```sh
$ cd django-restful/v01/dockerfiles
$ docker-compose up -d
```
3. Now, let's check it out
```
$ curl -i localhost/api/v1/hello
HTTP/1.1 200 OK
Server: nginx/1.14.2
Date: Fri, 24 May 2019 15:33:02 GMT
Content-Type: application/json
Content-Length: 14
Connection: keep-alive
Access-Control-Allow-Origin: *
Access-Control-Allow-Headers: X-Requested-With, Content-Type, X-Custom-Header
Access-Control-Allow-Methods: GET, POST, PUT, PATCH, DELETE

"Hello World"
```


## Features

* Python web server using Nginx and uWSGI
* Nginx plus HTTPS certificate generation with Let's Encrypt 


The final project structure will look like this: 

$ docker-compose ps

Name                  Command                          State          Ports
------------------------------------------------------------------------------------------------------------------------------
db                    docker-entrypoint.sh postgres    Up (healthy)   5432/tcp
elasticsearch         /docker-entrypoint.sh elas ...   Up             9200/tcp, 9300/tcp
kibana                /docker-entrypoint.sh kibana     Up             0.0.0.0:5601->5601/tcp
logstash              /docker-entrypoint.sh -e         Up             0.0.0.0:5044->5044/tcp
mq                    docker-entrypoint.sh rabbi ...   Up (healthy)   15671/tcp, 0.0.0.0:21072->15672/tcp, 25672/tcp, 4369/tcp, 5671/tcp, 0.0.0.0:2172->5672/tcp,0.0.0.0:32770->5672/tcp
nginx                 /usr/bin/supervisord -c /e ...   Up             0.0.0.0:443->443/tcp, 0.0.0.0:80->80/tcp
redis                 docker-entrypoint.sh redis ...   Up (healthy)   6379/tcp
web                   /usr/bin/supervisord -c /e ...   Up             0.0.0.0:8000->8000/tcp   
```


## Generate Api Doc
```.env
$ ./scripts/apidoc.sh
```


## Contributing

1. Fork it (https://github.com/trydirect/django-restful/fork)
2. Create your feature branch (git checkout -b feature/fooBar)
3. Commit your changes (git commit -am 'Add some fooBar')
4. Push to the branch (git push origin feature/fooBar)
5. Create a new Pull Request


## Support Development

[![Donate](https://img.shields.io/badge/Donate-PayPal-green.svg)](https://www.paypal.com/cgi-bin/webscr?cmd=_s-xclick&hosted_button_id=2BH8ED2AUU2RL)