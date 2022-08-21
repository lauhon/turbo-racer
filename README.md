# Turbo Racer

An open-source backend with a Web UI for managing your [Turborepo](https://turborepo.org/) cache.
## Features

There are a few open-source turborepo cache backends out there, but all of them seem to lack
management around tokens and teams. If you work in an enterprise, access management is crucial
for keeping permissions segregated and I could not find anything supporting that.

So I've build my own version called Turbo Racer. Besides giving you full control over
creating teams, issuing tokens for specific teams and who has access to a given token,
it also allows you to go from a simple deployment using your file system as artifact storage to
going full scale using a S3-compatible backend service.

Here is what is available for you:

- [x] Store artifacts
  - [x] Using file system
  - [x] Using S3 (Tested with the following)
    - [x] [Cloudflare R2](https://developers.cloudflare.com/r2/platform/s3-compatibility/api/)
    - [x] [AWS S3](https://aws.amazon.com/s3/)
- [x] Cache busting
  - [x]  Automatic artifact busting to keep your disk or your S3 bill sane.
    - [x]  Configurable busting period via environment variable (see `docker-compose.prod.yml`)
- [x] Management via a Web UI for
  - [x] Teams
  - [x] Tokens
  - [x] User sign-up/sign-in (Will refine this part with more permission controls)

## What is coming next

- [ ] User management to toggle user sign-up/sign-in
- [ ] Statistics dashboard

## Dependencies

To run this app locally, you need the following dependencies installed:

- [Elixir 1.13](https://elixir-lang.org/) and [Erlang OTP 25](https://www.erlang.org/)
  - You can quickly setup with [asdf](https://asdf-vm.com/) following this guide [here](https://thinkingelixir.com/install-elixir-using-asdf/).
- Postgres 14
  - The simplest way is to have [Docker](https://docs.docker.com/engine/install/centos/) installed and run `docker-compose up`.
    It will start up a Postgres container with a database ready for your dev server and for running tests.

## Starting development

To start your Phoenix server:

- Install dependencies with `mix deps.get`
- Create and migrate your database with `mix ecto.setup`
- Start Phoenix endpoint with `mix phx.server` or inside IEx with `iex -S mix phx.server`

Now you can visit [`localhost:4000`](http://localhost:4000) from your browser.

## Running tests

Make sure that the Postgres container is running and execute `mix test`

## Ready for Production

Turbo Racer is designed to be deployed with Docker. The simplest way is to use [docker-compose](https://docs.docker.com/compose/).
Have a look at the `docker-compose.prod.yml` in the root directory for an deployment example.
