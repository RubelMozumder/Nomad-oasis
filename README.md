# Installation of Nomad Oasis
## Some note for Nomad Oasis
### `Proxy` service
Service `Proxy` works as an intermediate server to communicate to the other services such as `app`, `worker`, and `north`. So requests follow the path **client-> Proxy Server-> Target Resources**, while without proxy server **client-> Target Resources**.
Attention to port `80:81` port `80` is the host port where your application is running (or client ports) and port `81` is for the service container here it is `proxy` service.
Also, check if the port on `nginx.conf` under `server->listen` is the same to the container port (here `81`). Because the service which is a proxy server and listen through the container port (`81`).  

### `north` Service
Check the host docker group id and fix the container ports for `user` which is the second port number followed by `:`. To check the host of the docker group ID, use the command `id` then you will get something 

```bash
uid=1000(<user>) gid=1000(<user>) groups=1000(<user>),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),122(lpadmin),134(lxd),135(sambashare),999(docker)
```
Where the docker group is `999`.

### Hardware considerations
1. **Storage**: Depends on the size of the data files.
2. **Storage Speed** Processing is designed as a synchronized task.
3. **Compute Resource** Four CPU cores are typically enough for a research group to run application, processing, and database operations in parallel.
4. **RAM** RAM is used for processing the metadata of individual files. The 2GB per core and at least 8GB are recommended also keep in mind that tools like `jupyter` need extra RAM and CPU.

4. **logtransfer** Service for transferring non-personalized data to nomad-developer team. The data comes in an anonymized from. The data mainly are used for
  a. Analyzing and monitoring system performance to identify and resolve issues.
  b. Improving our NOMAD software based on usage patterns.
  c. Generating aggregated and anonymized reports.

### User management system
There are two ways to use a user management system:
1. Central User Management (in central nomad installation)
2. Personalised User Management System
The Central User Management by `noamd-lab.eu` is the recommended one. The Central User management system does not communicate with Oasis directly and Oasis can be run without exposing it to the public internet. The user must be able to reach the Oasis after logging into Oasis user will be redirected to the Central User Management Server. After login to the Central Management Server user will be redirected to the Oasis back. Central User Management will help to synchronize the data between the NOMAD installations e.g. Oasis. This Central User Management can be used for data shearing between different users using different Oasis. 



