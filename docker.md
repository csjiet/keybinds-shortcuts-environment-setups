1. Create and start the Rocket linux docker
2. Install packages using dnf
3. `docker ps`
4. Copy container id 
5. Commit the container state to a new image: `docker commit 2250 ytang/os-with-neovim`
6. Use the updated image


## Copy current image to a new image

1. `docker ps`
2. `docker commit <container-id> <new-image-name>`
	- E.g.,  `docker commit 6bf4d376c87c ytang/os-updated`

## Start a session
1. `docker start <container-id>`

## Continue a session
2. `docker ps`
3. `docker attach <container-id>`

## Start a new shell/ session to edit the same file
4. `docker exec -it 2250-nvim /bin/bash`
