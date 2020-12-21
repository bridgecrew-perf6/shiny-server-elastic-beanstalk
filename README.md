##Use this to deploy shiny server 'manually' via the Elastic Beanstalk UI
####Created this as I encountered [this issue](https://github.com/aws/aws-elastic-beanstalk-cli/issues/53) deploying via ELB CLI

#####TODO
- [ ] Add instructions for deploying to Elastic beanstalk
- [ ] Add instructions for testing locally

1. Create a new folder named **myapp** under the **apps** folder
    The new folder directory should look like:
    ```bash
    shiny-server-app/--
        /apps
            /hello-app
            /myapp
        Dockerfile
        Dockerrun.aws.json
        shiny-server.sh
        .dockerignore
        .gitignore
    ```
2. Copy all your shiny app code + files into the **myapp** folder

3. In the root folder (shiny-server-app) run the below to create a zip file:
    ```bash
     zip -r deployment.zip .   
    ```
   
5. The **deployment.zip** file is the file you will upload to elastic beanstalk