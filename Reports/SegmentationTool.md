# Intel: Computer Vision Annotation Tool (CVAT)
## Attributes
<ul>
    <li>browser-based application (only chrome)</li>
    <li>Can work with team on</li>
    <li>Object detecten, image classification, image segmentation</li>
    <li>Can be installed using Docker</li>
</ul>

## Getting started
https://openvinotoolkit.github.io/cvat/docs/

### Installation
I can't seem to upload any images on [cvat website](https://cvat.org/). <br>
It seems I have to build a container with the CVAT source code in. I can do this by using docker.
```
Creating network "cvat_cvat" with the default driver
Creating volume "cvat_cvat_db" with default driver
Creating volume "cvat_cvat_data" with default driver
Creating volume "cvat_cvat_keys" with default driver
Creating volume "cvat_cvat_logs" with default driver
Pulling cvat_db (postgres:10-alpine)...
10-alpine: Pulling from library/postgres
Digest: sha256:419780ee7b953bc9ef3d45846b76195ee3a1d2808d5e9a702e8f701bd35d34a6
Status: Downloaded newer image for postgres:10-alpine
Pulling cvat_redis (redis:4.0-alpine)...
4.0-alpine: Pulling from library/redis
Digest: sha256:aaf7c123077a5e45ab2328b5ef7e201b5720616efac498d55e65a7afbb96ae20
Status: Downloaded newer image for redis:4.0-alpine
Pulling cvat (openvino/cvat_server:)...
latest: Pulling from openvino/cvat_server
Digest: sha256:f76be83e1ecd6952eb87d69dbbc5141ad57db81614fceec50484bcc985b340bb
Status: Downloaded newer image for openvino/cvat_server:latest
Pulling cvat_ui (openvino/cvat_ui:)...
latest: Pulling from openvino/cvat_ui
Digest: sha256:5ce3e3dce0d9867ccc214ca29657e9e188d51abedefe0109a315cd2f642ca686
Status: Downloaded newer image for openvino/cvat_ui:latest
Pulling traefik (traefik:v2.4)...
v2.4: Pulling from library/traefik
Digest: sha256:840e948af3c8d1e45e986eee7d97004ab29cfccffdf0be4c116ba9aaeff5d17a
Status: Downloaded newer image for traefik:v2.4
Creating traefik ...
Creating cvat_db ...
Creating cvat_redis ...
Creating cvat_db    ... done
Creating cvat_redis ... done
Creating cvat       ...
Creating traefik    ... done
Creating cvat       ... done
Creating cvat_ui    ...
Creating cvat_ui    ... done
```

I needed to make a superuser that is able to create tasks. I assume that is the reason why I couldn't upload any images to annotate.
```
$ winpty docker exec -it cvat bash -ic 'python3 ~/manage.py createsuperuser'
System check identified some issues:

WARNINGS:
?: (urls.W005) URL namespace 'v1' isn't unique. You may not be able to reverse all URLs in this namespace
Username (leave blank to use 'django'): NickAdmin
Email address: nick.dw@hotmail.com
Password:
Password (again):
Superuser created successfully.
```

Now when I navigate to [localhost:8080](http://localhost:8080/) I see the CVAT website and I am able to upload an image now!

### First annotation
Now I can open a task and start to annotate images. I needed to save and than export the task dataset under 'Menu'.<br>
The format I requested was COCO 1.0. Then a download starts and I get the image and the annotation in json format, more specifically the COCO 1.0 version.

## What I know
The annotation tasks will be done by Viu More and that's why it needs to be accessed easily for Viu More employees.

## I wonder...

| Question, thought, assumption or a double check | Answer |
| -- | -- |
| For the segmentation of images for Renewi I assume the annotation tool will run on the cloud. This will not run on the image captation device itself. | True, more specifically the tool wil run on a VM that will be running in the cloud. |
| The output data of CVAT is more than enough for the model and doesn't need to be transformed anymore. |  |
| The desired output format is json COCO 1.0 | |

