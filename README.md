# Use this to deploy shiny server 'manually' via the Elastic Beanstalk UI

## Created this as I encountered [this issue](https://github.com/aws/aws-elastic-beanstalk-cli/issues/53) deploying via ELB CLI

### TODO
- [x] ~~Add instructions for deploying to Elastic beanstalk~~
- [ ] Add instructions for testing locally
- [ ] Add instructions for mounting persistent storage for apps
- [ ] Add ui for users to upload apps to the shiny server


## Instructions

### Local Setup
1. Clone this repo via the command line:
    ```bash
    git clone https://github.com/ranvirm/shiny-server-elastic-beanstalk.git
    ```
   
2. Navigate into the cloned folder
    ```bash
   cd shiny-server-elastic-beanstalk/
   ```

3. Create a new folder named **myapp** under the **apps** folder
    ```bash
   mkdir ./apps/myapp 
   ```
    The new folder directory should look like:
    ```bash
    shiny-server-elastic-beanstalk/
        /apps
            /hello-app
            /myapp
        Dockerfile
        Dockerrun.aws.json
        shiny-server.sh
        .dockerignore
        .gitignore
    ```
4. Copy all your shiny app code + files into the **myapp** folder
    ```bash
    cp -R ..path_to_your_app/* ./apps/myapp
   ```

5. In the root folder (**shiny-server-elastic-beanstalk/**) run the below to create a zip file:
    ```bash
     zip -r deployment.zip .
    ```
   
5. The newly created **deployment.zip** file is the file you will upload to elastic beanstalk

### Elastic Beanstalk Deployment
1. Navigate to the Elastic Beanstalk UI in the AWS console

2. Click **Create a new Environment**

3. Select **Web server environment** and click **Select**

4. Fill in the required fields:
    1. Application name: **shiny-server-1** (or whatever you want)
    2. Environment name: **shiny-server-env-1** (or whatever you want)
    3. Under **Platform**
        1. Select **Managed platform**
        2. Under **Platform** select **Docker**
        3. Leave the populated values as default
    4. Under **Application code**:
        1. Select **Upload your code**
        2. Enter a version: **1.0** (or whatever you want)
        3. Select **Local file**
        4. Click **Choose file** and upload your zipped deployment file that you created earlier: **deployment.zip**
5. Click **Create Environment** \
*This will begin the deployment and may take a few minutes to complete*

6. Once the deployment has completed you will be presented with a url to the shiny server

    Going to the url will open up the shiny server homepage
    
    Add **/apps/myapp/** to the end of the homepage url to view your app or the sample app with **/apps/shiny-app/**
