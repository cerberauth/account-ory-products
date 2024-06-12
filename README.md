# Ory Products Starter Kit

## Overview

This repository contains a starter kit for Ory products. It is a collection of Docker Compose files that can be used to start with [Ory products](https://www.ory.sh/) quickly.

## Prerequisites

- [Docker](https://docs.docker.com/get-docker/)
- [Docker Compose](https://docs.docker.com/compose/install/)

### Products

- **Identity and User Management (CIAM)**: [Ory Kratos](https://www.ory.sh/docs/kratos/ory-kratos-intro)
- **OAuth 2.0 and OpenID Connect Provider**: [Ory Hydra](https://www.ory.sh/docs/oauth2-oidc)
- **Permission and Role Management (implementation of Zanzibar)**: [Ory Keto](https://www.ory.sh/docs/keto) (coming soon)
- **Identity and Access Proxy (IAP)**: [Ory Oathkeeper](https://www.ory.sh/docs/oathkeeper)

## Usage

1. Clone this repository:

```bash
git clone https://github.com/cerberauth/account-ory-products.git
cd account-ory-products
```

2. Configure a local domain for the services. Add the following line to your `/etc/hosts` file:

```bash
127.0.0.1 auth.example.localhost
127.0.0.1 oauth.example.localhost
```

3. Copy the `.env.example` file to `.env`:

```bash
cp .env.example .env
```

Edit the `.env` file and set the values for the environment variables. If you have any doubts, you can check the according Ory documentation for each product.
In order to generate secure values for the environment variables, you can use the following command:

```bash
openssl rand -base64 32
```

3. Start the services:

```bash
docker-compose -f docker-compose.yml -f docker-compose-kratos.yml up -d
```

If you want to start Hydra, you can use the following command:

```bash
docker-compose -f docker-compose.yml -f docker-compose-hydra.yml -f docker-compose-kratos.yml up -d
```

4. Access the services: [http://auth.example.localhost/welcome](http://auth.example.localhost/welcome)

For your new OpenID Connect Provider, you will have to create a new OAuth 2.0 client. You can do this by following the [Ory Hydra documentation](https://www.ory.sh/docs/hydra/guides/oauth2-clients).
