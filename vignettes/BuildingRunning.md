## Background

-   Linux servers and their [specs](https://www.st.nmfs.noaa.gov/confluence/display/NECIT/Linux+Servers+at+the+NEFSC).

-   The first two servers have podman and docker installed respectively.

-   You will need an account/permissions set up for you (by ITD) to use either

-   Both podman and docker operate in an almost identical way. You can just switch the word podman for docker and vice-versa in any proceeding examples

-   You will need to use VPN and log in to one of the servers, preferably using powershell (windows) or terminal (mac, linux)

-   ssh [username\@server.nefsc.noaa.gov](mailto:username@server.noaa.nefsc.gov){.email}

## Build. Run. Use

-   Copy/write `Dockerfile` into a project directory. (The file must have the name `Dockerfile`).

-   Navigate to that directory.

-   Build Docker image (don't forget the period)

    > docker build -t test_image .

    If you encounter a message regarding the `daemon` and related permissions it means that you do not have suficient permissions. You will need to be added to the docker user group. Reach out ITD.

-   Run container

    > docker run -dp 8787:8787 -e PASSWORD=yorpassword -e USERID=\$UID `--`mount "type=bind,src=\$PWD,dst=/home/rstudio/proj1" test_image

    Note: yourpassword, proj1 and test_image are user selected names This will mount your current working directory (your project directory on the server with all nested folders and files) to a `proj1` folder inside the container. All work created in the container will be copied to the server. All new work created inside your current working directory will be accessible inside the container.

-   Some docker commands

    > docker images  (view all created images)
    >
    > docker image rm <image ID>  (remove created images)
    >
    > docker container ls      ( view all running containers)
    >
    > docker stop <container ID> (stop container)
    >
    > docker rm <container ID>  (remove stopped container)
    >
    > docker ps -a   (view all stopped containers)
    

-   Log in to running container. Open a web browser and go to serverURL:8787. Username = `rstudio`, password = whaterver you selected for `yourpassword`

## 
