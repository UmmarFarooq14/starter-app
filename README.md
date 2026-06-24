# starter-app
A simple hello-world web application with a stateful backend, built using Docker and Docker Compose. Designed as a Kubernetes support training project, it serves as a starting point for converting a containerized application into Kubernetes resources such as Deployments, Services, ConfigMaps, Secrets, and StatefulSets with persistent storage.

# Architecture:

                        +-------------------+         +------------------------+
             client -> |  web (Flask app)  |  -->    |  redis (visit counter) |
                        |  stateless        |         |  stateful + volume     |
                        +-------------------+         +------------------------+
                                |                               |
                          app.config.env                    redis-data
                          + .env (secret)                  (persistent volume)

    . web — a stateless Flask app served by gunicorn. Later: a Deployment + Service.
    . redis — a stateful key/value store that holds a visit counter on a persistent volume. Later: a StatefulSet + PersistentVolumeClaim.



# What it is:
 

     A small Flask app served by gunicorn, backed by Redis. There is no authentication, no real database, no queues, and no background jobs — just three routes, a visit counter, and a clean split between configuration and secrets.

# Routes:

