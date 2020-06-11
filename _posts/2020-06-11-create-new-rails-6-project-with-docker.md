---
layout: post
title: Create new Rails 6 project with Docker
date: 2020-06-11 17:41 +0100
---

If you want to set-up a new Rails project, but you don't want to go through the hassle of setting op Ruby, node, Yarn, Rails itself, etc. you could do it with Docker. That way you can really fast start a new project, without possible version conflicts, installs, etc. on your computer...

Let's go! 🚀

## Prerequisite: Have Docker installed

If not, [install Docker](https://hub.docker.com/search/?type=edition&offering=community) first

## Create the directory for your project

Open a terminal, create a project folder somewhere and go into that directory:

```bash
mkdir my_rails_project ; cd my_rails_project
```

## Setup your project

First, you need to start a container to open your folder with, to install Rails.
Run your container:

```bash
docker run --rm -v ${PWD}:/usr/src -w /usr/src -ti starefossen/ruby-node /bin/bash
```

Within the container, install Rails first:

```bash
gem install rails
```

After installing Rails, create you project. Because your container working directory is bound to you project folder, the Rails project will be created there:

```bash
rails new .
```

_(mind the . at the end! This will install the project in the current directory)_

After creating the project, close your container with `exit`.  Your container will be closed and removed. And you'll end up with a shiny new Rails install, without having Rails, Ruby, etc. on your computer.

## Create a Dockerfile

Next, to Run your project, create a `Dockerfile` file in the root of your project, and paste the following (or whatever setup you'd prefer) in that file:

```Dockerfile
FROM starefossen/ruby-node

# Set the workdir inside the container
WORKDIR /usr/src/app

# Set the gemfile and install
COPY Gemfile* ./
RUN bundle install

# Copy the main application.
COPY . ./

# Expose port 3000 to the Docker host, so we can access it
# from the outside.
EXPOSE 3000

# The main command to run when the container starts. Also
# tell the Rails dev server to bind to all interfaces by
# default.
CMD ["bundle", "exec", "rails", "server", "-b", "0.0.0.0"]
```

## Build you container

Build a shiny new Docker container, based on a [Ruby + Node Docker Image](https://hub.docker.com/r/starefossen/ruby-node), having your project in there, executed on launch:

```bash
docker build -t my_project .
```

## Run your container

Execute:

```bash
docker run \
-p 3000:3000 \
-v $(pwd):/usr/src/app/ \
my_project
```

This runs your built container, forwarding port 3000 and connects the current folder (your project folder) to the one inside the container (so you can edit files while it is running).

## Check it out

Open your browser en go to [http://localhost:3000](http://localhost:3000) Yay! You’re on Rails! 🚂

### Log in to your container

If you want to go inside your container (to create controllers, views, models, etc.) run:

```bash
docker exec -it $(docker ps -q) /bin/bash
```

This will execute an interactive (so you can actually use it) /bin/bash inside the running container. 

That's all for now! 👋