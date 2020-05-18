---
layout: post
title: Deno in Docker on Google Cloud Run
date: 2020-05-18 19:12 +0100
category: Tech
---
This weekend I read a lot about [Deno](https://deno.land), "_A secure runtime for JavaScript and TypeScript_." It's built on V8 and Rust, by Ryan Dahl, the creator of Node.js and it would basically ['fix' many things that are 'wrong' about Node.js and would be a "fun and productive scripting environment"](https://deno.land/v1).

It intrigued me, so I took a first look 😊

## Playing around

After some [playing](https://deno.land/manual) and reading ([this is an amazing source!](https://www.freecodecamp.org/news/the-deno-handbook/)) I figured it would be nice to have an easy starting point for a Deno project running inside Docker and also on Google Cloud Run.

## Deno in Docker (on Cloud Run)

I wanted to make a concrete example of Deno, running on Cloud Run. So I build just that. A "Hello world" of Deno, with a Dockerfile (that pre fetches all dependencies) to easily run it anywhere + deployment to Cloud Run.

You can see the result here: [https://github.com/rogiervandenberg/deno-docker-cloudrun](https://github.com/rogiervandenberg/deno-docker-cloudrun) Of course with an easy single click deployment button 🎉