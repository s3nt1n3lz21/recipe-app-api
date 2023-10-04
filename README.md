# recipe-app-api
Recipe API

# Structure

                   AWS EC2 Instance
┌─────────────────────────────────────────────────────────┐
│                                                         │
│  ┌───────────────────────────────────────────────────┐  │
│  │                  Volumes                          │  │
│  │ ┌──────────────┐ ┌─────────────┐ ┌─────────────┐  │  │
│  │ │Postgres Data │ │Static Files │ │ Media Files │  │  │
│  │ └──────▲───────┘ └───▲───▲─────┘ └─▲────▲──────┘  │  │
│  │        │             │   │         │    │         │  │
│  └────────┼─────────────┼───┼─────────┼────┼─────────┘  │
│           │             │   │         │    │            │
│           │             │   └─────────┼─┐  │            │
│           │             │             │ │  │            │
│           │             ├─────────────┘ │  │            │
│           │             │               │  │            │
│           │             │     ┌─────────┴──┴───────┐    │
│   ┌───────┴────┐        │     │   uWSGI App Server │    │
│   │  Dockerised│        │     │  ┌─────────────┐   │    │
│   │  PostGres  │        │     │  │  Dockerised │   │    │
│   │  Database  │        │     │  │  Python     │   │    │
│   │            │        │     │  │  Django API │   │    │
│   └──────▲─────┘        │     │  │  App        │   │    │
│          │              │     │  └─────────────┘   │    │
│          │              │     │                    │    │
│          │              │     └──────────▲─────────┘    │
│          │              │                │              │
│          │              │                │              │
│          │       ┌──────▼─────────┐      │              │
│          │       │  Dockerised    │      │              │
│          └───────┤  Nginx Reverse ├──────┘              │
│                  │  Proxy         │                     │
│                  │  Server        │                     │
│                  └───────▲────────┘                     │
│                          │                              │
│                          │                              │
│                          │                              │
└──────────────────────────┼──────────────────────────────┘
                           │

# Testing
Run unit tests on the dockerised app using

docker-compose run --rm app sh -c "python manage.py test"

# Deployment
SSH Connect to our EC2 Instance
Install Docker and other stuff
Setup An SSH Key On the EC2 Instance
Use the SSH Key to allow the EC2 Instance to download the github repo code
Execute Git clone Command To Copy The Github Code To The EC2 Instance
Setup The .env file on the EC2 Instance


