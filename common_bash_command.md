## Common Bash Commands

### File and Directory Operations

### Checking Port Availability
#Check which ports are open
```bash
netstat -tuln
```

#Check if a specific port is open
```bash
netstat -tuln | grep :<port_number>
```

#Check if a specific port is open (alternative)
```bash
lsof -i :<port_number>
```

# Downloading Files
# List all running containers
```bash
docker ps -a
```
# Check logs of a specific container
```bash
docker logs <container_id> sh
```

# Check logs of a specific container (alternative)
```bash
docker exec -it server-gkw4sc0kwokw8kwwok0gocsw-190816991224 sh
```

# Enter the container shell and its postgres database
```bash
docker exec -it <container_name> psql -U admin -d postgres -c "\du"
```



# Check DNS resolution
```bash
dig n8n.bio-centra.com +short   
```


```bash
curl -I http://n8n.bio-centra.com +o history
```

```bash
Notes:
POSTGRESQL-work-space

POSTGRES_PORT=5432
POSTGRES_SUPERPASS=postgresqlBioCentra2025!!
POSTGRES_SUPERUSER=admin

https://github.com/HPABio/work_stack.git

docker exec -it  sh           

postgresql-mccogkg480o40wwkwssk4s8g-223657707597
root@srv814301:~# redis://redis:6379
root@srv814301:~# s:6379: No such server-gkw4sc0kwokw8kwwok0gocsw-212943709202  sh
root@srv814301:~# docker exec -it server-gkw4sc0kwokw8kwwok0gocsw-212943709202 sh                                 
apk add busybox-extras # if Alpine
/app/packages/twenty-server $ apk add busybox-extras
ERROR: Unable to lock database: Permission denied
ERROR: Failed to open apk database: Permission denied
/app/packages/twenty-server $ nc -zv redis 6379
redis (10.0.6.4:6379) open
/app/packages/twenty-server $ Command 'apk' not found, did you mean:
  command 'ark' from snap ark (25.04.0)
  command 'ack' from deb ack (3.7.0-1)
  command 'apt' from deb apt (2.7.6)
  command 'ark' from deb ark (4:23.08.4-0ubuntu1)
  command 'awk' from deb gawk (1:5.2.1-2)
  command 'awk' from deb mawk (1.3.4.20231126-1)
  command 'awk' from deb original-awk (2023-11-27-1)
  command 'apg' from deb apg (2.2.3.dfsg.1-5build2)
See 'snap info <snapname>' for additional versions.
nc: getaddrinfo for host "redis" port 6379: Temporary failure in name resolution
root@srv814301:~# 

services:
  redis:
    image: r


    docker ps --format "table {{.Names}}\t{{.Image}}"




-- Terminate connections to drop the DB
SELECT pg_terminate_backend(pid) FROM pg_stat_activity WHERE datname = 'calcom';

DROP DATABASE IF EXISTS calcom;
CREATE DATABASE calcom OWNER calcom_user;

\connect calcom

GRANT USAGE ON SCHEMA public TO calcom_user;
GRANT CREATE ON SCHEMA public TO calcom_user;
ALTER DEFAULT PRIVILEGES IN SCHEMA public GRANT ALL ON TABLES TO calcom_user;



docker exec -it <container_name> sh
npx prisma migrate deploy