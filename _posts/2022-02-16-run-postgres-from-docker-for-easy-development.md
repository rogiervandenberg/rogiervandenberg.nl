---
layout: post
title: Run Postgres from Docker for easy development
date: 2022-02-15 08:05 +0000
category: Development
---

_Postgres is a great database server that you can install locally on your computer for development. However, there are various ways in which you can install PostgreSQL on your machine, e.g. by using the the [installer](https://www.postgresql.org/download/macosx/), [homebrew](https://formulae.brew.sh/formula/postgresql) or [postgres.app](https://postgresapp.com/). But managing your local Postgres is a real pain. "What was the command again to stop/start the service?", "Do you need to have it always be running in the background (even when you are not working)?", "How to handle multiple versions next to each other?", "How to handle updates?"_

→ What if I tell you, **you can run Postgres in one command, in any version WITHOUT having to install it in your machine? WITH the benefit of persisting data?** That would be a total game changer! 😃

## Docker

Docker allows you to put software in a container and run it with a single command. You could make your own image that packs an operating system, your settings/preferences and your application into a container for easy deployment, but, you can also use a pre-build image to run things like a database engine!

## Run a local Postgres with Docker

Let's say I need to have Postgres in the specific (old) version 9.6 and the databases should be persisted outside the container on my local computer.

### Install Docker

First, make sure you have Docker installed on your computer: https://docs.docker.com/get-docker/

### Create a local directory to persist the data in

In my example, I'm going to write the database to my `/tmp` folder, but this can be anywhere.

`mkdir /tmp/database`

_A better place would be a subfolder in your project, or in your home-dir._

### Start Postgres with Docker

```shell
docker run --rm -it \
-p 5432:5432 \
-e POSTGRES_PASSWORD=password \
-v /tmp/database:/var/lib/postgresql/data:delegated  \
postgres:9.6
```

Let me break down what this does:

- Run a container and clean up afterwards and allow the process to be interactive (so you can cancel it when you're done)
- Allow connections to the Postgres inside the container on port 5432 from the outside of the container on port 5432
- Set the default password for the postgres user to `password`
- Sync all stored data of Postgres inside the container into our local folder `/tmp/database` (make sure this folder exists!). "Delegated" means that the container’s view of the file system will be authoritative, as we won't be changing the data from outside the container, so the database will be quick.
- Use the Postgres 9.6 image

### Connect!

Now, you can connect to `localhost` on port `5432`, with default username `postgres`, password `password` and default database `postgres`.

A great and easy way to connect to your database is with the [TablePlus app](https://tableplus.com/) (for Mac, Windows, Linux and more!):

![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644938235070/_L_MoPGAQ.png)

### Stopping

If you're done working, just `CTRL-C` out of your database. The container will be cleaned up and Postgres is gone again. But, your data is still save on your own computer.

Next time you execute the above `docker run` command, Postgres will be fired up again; Really fast if it is still cached on your computer, otherwise quite fast by downloading the image again:
![image.png](https://cdn.hashnode.com/res/hashnode/image/upload/v1644938844472/3KwA9BZm7.png)
