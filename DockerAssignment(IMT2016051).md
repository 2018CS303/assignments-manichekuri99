# Docker Case Study

1. list of users.
>username.txt
 ```
user1
user2
user3
```
2. To create docker container for each user.
>create_containers.sh
 ```sh
echo -n "Enter file name:"
read filename
while read username
    do
      docker create -it --name $username docker_image /bin/bash
    done < $filename
```

3. To use the allocated containers.
>use_container.sh
```sh
echo -n "Enter username of a container:"
read username
docker start $username
docker attach $username
```

4. Monitor the containers.
>monitor_container.sh
```sh
echo -n "Enter username of the container to be monitored:"
read username
docker logs -f $username
```

5. Delete the containers
>delete_container.sh
 ```sh
echo -n "Enter file name:"
read filename
while read username
    do
      docker stop $username
      docker rm $username
    done < $filename
```
