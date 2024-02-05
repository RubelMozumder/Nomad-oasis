# Installation of Nomad Oasis
## Some note for Nomad Oasis
### `Proxy` service
Service `Proxy` works as an intermediate server to communicate to the other services such as `app`, `worker`, and `north`. So requests follow the path **client-> Proxy Server-> Target Resources**, while without proxy server **client-> Target Resources**.
Attention to port `80:81` port `80` is the host port where your application is running (or client ports) and port `81` is for the service container here it is `proxy` service.
Also, check if the port on `nginx.conf` under `server->listen` is the same to the container port (here `81`). Because the service which is a proxy server and listen through the container port (`81`).  
   
