## Directory Structure

    odoo_docker
    	-- addons/   #   <---- custom_addons are here
    	-- db.env
    	-- docker-compose.yml
    	-- odoo.env
	


## Some Docker Commands
    
    # Build containers
	docker-compose up --build
		
    # Start containers up in the background
	docker-compose up -d

	# Restart containers
	docker-compose restart

    # Stop containers
    docker-compose stop
    
    # Destroy containers (WARNING: This could mean data inside those containers as well)
    docker-compose down
    
    # Show container processes
    docker ps
    
    # Show container process stats
    docker stats
    
    # SSH into a container
    docker exec -it {container_id} sh
    
    # Copy contents to container from host
    docker cp ~/my/file {container_id}:~/myfile
    
    # Copy contents from container to host
    docker cp {container_id}:~/myfile ~/my/file
    
    # Tail the process from a container
    docker logs -f {container_id}
    
    # Run command inside container
    docker exec {container_id} command
    
    ## Odoo Examples
    docker exec {container_id} /usr/bin/odoo scaffold module_name /mnt/extra-addons
    docker exec {container_id} /usr/bin/odoo -u all -d odooDB
    
    # Remove all stopped containers, all dangling images, and all unused networks
    docker system prune
    
    # Remove all unused volumes
    docker system prune --volumes
    
    # List all containers
    docker container ls -a
    
    # Remove container
    docker rm {container_id}
    
    # List all images
    docker image ls
    
    # Remove image
    docker rmi {image_id}
    
    # List all volumes
    docker volume ls
    
    # Remove volume
    docker volume rm {volume_name}
    
