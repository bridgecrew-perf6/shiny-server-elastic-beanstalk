1. Copy all your shiny app code + files into the 'shiny-app' folder

2. Rename the 'shiny-app' folder to your app name - assuming new name is bond-sales

    The new folder directory should look like:
    ```bash
    shiny-server-app/--
        /hello-app
        /bond-sales
        Dockerfile
        Dockerrun.aws.json
        shiny-server.sh
        .dockerignore
        .gitignore
    ```
3. Update the Dockerfile with the folder name change you made above:

    Change this
    ```bash
    COPY shiny-app /srv/shiny-server/shiny-app
    ```
    To this
    ```bash
    COPY bond-sales /srv/shiny-server/bond-sales
    ```
4. In the root folder (shiny-server-app) run the below to create a zip file:
    ```bash
     zip -r deployment.zip .   
    ```
   
5. The **deployment.zip** file is the file you will upload to elastic beanstalk