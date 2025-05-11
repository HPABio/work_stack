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
