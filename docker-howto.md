# Docker Reference

Docker [reference](https://docs.docker.com/reference/)

# Admin

[Post Instal Setup](https://docs.docker.com/engine/install/linux-postinstall/)
Also
 * Run from any user in docker group
 * Configure to start on boot


# useful images

[Fake SMTP Server](https://hub.docker.com/r/reachfive/fake-smtp-server)


Open speed test

    sudo docker run --restart=unless-stopped --name=openspeedtest -d -p 80:8080 openspeedtest/latest
    # Start from local, don't delete
    sudo docker run -p 8080:8080 openspeedtest/latest

# Commands

## Images

Pull an image

	docker pull user/image:tag
	

List images

	docker images

Prune images

	docker image prune

Look at the contents of an image

	docker run -it -rm image_name bash



## Containers

List containers

	docker container ls

	-a for all
	--help for help

Stop a container

	docker container stop .name.

Start a container 

	docker container start .name.

delete a container

	docker container rm .name.
	
Prune containers

	docker container prune

Attache to the main stdin, stdout, and stderr of a container

	docker container attach .name.

Run a command in a container.  Here `bash` is run

	docker container exec -it container_name bash 

 * `-it` for interactive
 * `--rm` to remove after run
 * 


## Volumes

### Copy and backup

Docker says to use a container to [tar and un-tar](https://docs.docker.com/storage/volumes/)

	from_vol=$1
	to_vol=$2
	transfer_image=ubuntu

	set -x
	docker volume create $from_vol
	docker run --rm -v $from_vol:/source --mount type=bind,source=$(pwd),target=/backup $transfer_image bash -c "tar cvf /backup/$to_vol.tar /source"
	docker run --rm -v $to_vol:/dest --mount type=bind,source=$(pwd),target=/backup $transfer_image bash -c "cd /dest && tar xvf /backup/$to_vol.tar --strip 1"
	rm $to_vol.tar


## Building

Build an image and give it a name and tag.


	docker build -t tomunger/homesolargather:0.1.0 .


List buildx platforms

	docker buildx ls

Some mac multi [architecture instructions](https://cloudolife.com/2022/03/05/Infrastructure-as-Code-IaC/Container/Docker/Docker-buildx-support-multiple-architectures-images/)

Setup steps:

	docker buildx create --name mybuilder --use

`--name` gives it a name and `--use` tells it to switch to the builder

	docker buildx inspect --bootstrap

Pulls something, - the build kit I guess.

Some platform names:  amd64, arm32v5, arm32v6, arm32v7, arm64v8, i386, ppc64le, and s390x



# Useful containers

[Fake SMTP Server](https://hub.docker.com/r/reachfive/fake-smtp-server)


# Postgres

	docker pull postgres

	docker run --rm   --name SW-pg -e POSTGRES_PASSWORD=TkFV3g8gu4 -d -p 5432:5432 -v $HOME/docker/volume/sw-pg/:/var/lib/postgresql/data

## PGAdmin

Pull container

	docker pull dpage/pgadmin4

	docker run --name pgadmin -e PGADMIN_DEFAULT_EMAIL=pg@tumtum.com -e PGADMIN_DEFAULT_PASSWORD=pgadmin -p 5443:443 -p 5080:80 dpage/pgadmin4

Runs the container named `pgadmin`.  Sets username and password.  Maps host port 5080 to container port 80 and 5443 to container port 443
    ?
