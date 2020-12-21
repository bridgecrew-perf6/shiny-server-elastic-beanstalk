# Use this to deploy shiny server 'manually' via the Elastic Beanstalk UI

## Created this as I encountered [this issue](https://github.com/aws/aws-elastic-beanstalk-cli/issues/53) deploying via ELB CLI

### TODO
- [ ] Add instructions for deploying to Elastic beanstalk
- [ ] Add instructions for testing locally


## Instructions
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

6. Navigate to teh Elastic Beanstalk UI in the AWS console

6. Click **Create a new Environment**

7. Select **Worker environment** and click **Select**

8. Fill in the required fields:
    1. Application name: **shiny-server-1** (or whatever you want)
    2. Environment name: **shiny-server-env-1** (or whatever you want)
    3. Under **Platform**
        1. Select **Managed platform**
        2. Under **Platform** select **Docker**
        3. Leave the populated values as default
    4. Under **Application code**:
        1. Select **Upload your code**
        2. Enter a version; **1.0** (or whatever you want)
        3. Select **Local file**
        4. Click **Choose file** and upload your zipped deployment file that you created earlier: **deployment.zip**
9. Click **Create Environment** \
*This will begin the deployment and may take a few minutes to completer*
10. Once the deployment has completed you will be presented with a url to the shiny server \

Going to the url will open up the shiny server homepage\

Add **apps/myapp/** to the end of the homepage url to view your app or the sample app with **apps/shiny-app/**
