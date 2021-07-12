# azure-cms-setup

This project was done as part of my coursework at Udacity in pursuit of completing an Nanodegree in Azure Cloud Development.  I was issued a challenge scholarship then received a full scholarship from Bertelsmann. In the project we were tasked with deploying a working CMS with login and creating / deploying the following:

- A webapp using Python with the Flask framework.
- A SQL database that contains a user table and an article table for the webapp to query.
- A Blob Storage container where images are stored.
- An authentication option to Sign in with your Microsoft account.
- Logging of successful and unsuccessful login attempts

## Explanation of the files below:

Below are some of the implementation files and deliverables that were required in completing this project. Some of the images were provided as proof that everything was operating on the back end as it was supposed to and some were added for illustrative purposes by me. 'views-here' and 'init.py' where added here to show the logging and MSAL implementation. Below the images is a rational I had to write up for choosing to deploy the application in the way I did. 



Here is an example of logging in using a user account specific to this CMS - user data is stored and red form a SQL Database hosted in Azure:
![Login](https://github.com/fullmetalfenix/azure-cms-setup/blob/main/imgs/standard-login.gif)


After registering an application with Azure Active Directory (AAD) you can implement OAuth 2.0 sign in through Microsoft Authentication Library (MSAL):
![Login](https://github.com/fullmetalfenix/azure-cms-setup/blob/main/imgs/MSAL-Quick.gif)


Here we can add a post, storing the text of the post in an SQL Database in Azure that holds Article and User data. We can also store images in an Azure Blob Storage container.
![Login](https://github.com/fullmetalfenix/azure-cms-setup/blob/main/imgs/add-a-post.gif)


Here is an example of editing a past article - recalling the data from the DB / Storage.
![Login](https://github.com/fullmetalfenix/azure-cms-setup/blob/main/imgs/blob-storage.gif)

Here are some successful / unsuccessful login attempts getting logged:
![Login](https://github.com/fullmetalfenix/azure-cms-setup/blob/main/imgs/logins.PNG)

Here is the setup for the applications blob storage account:
![Login](https://github.com/fullmetalfenix/azure-cms-setup/blob/main/imgs/sql-storage-solution.JPG)





## Project Write up (part of the assignment)


### Analyze, choose, and justify the appropriate resource option for deploying the app.

*For **both** a VM or App Service solution for the CMS app:*
- *Analyze costs, scalability, availability, and workflow*
- *Choose the appropriate solution (VM or App Service) for deploying the app*
- *Justify your choice*

### Assess app changes that would change your decision.

*Detail how the app and any other needs would have to change for you to change your decision in the last section.* 


When considering multiple factors, cost for the App service solution can be lower than the cost of a VM. This is taking into consideration not only the infrastructure cost of a VM vs an app service plan but also the cost of staff required to maintain and patch the server as well. One thing that should be taken into consideration when selecting between the two is that VM's can help you avoid vendor lock in so if you find a cheaper host in the future you can more easily transfer between the two. Both options are less expensive than buying your own hardware and running it, maintaining it and securing it physically. Both VM's and app service plans have high availability and can scale but only the App service plan can be set to scale horizontally and vertically automatically as compared to the VM which can also scale but is more difficult with multiple VM's having to be deployed as well as load balancing and other considerations that an app service plan does not require. As far as workflow the VM is much more labor intensive as you have to configure the underlying infrastructure of the application and maintain it yourself compared to the app service which takes minimal setup as well as has simple setup for continuous integration/deployment options. VM's are much more versatile than app services as app services have a limited set of supported languages and OS options. Additionally VM's are better at legacy applications as you can completely control the environment to ensure compatibility with the application. 

I chose to host on an app service plan as this is a small demo project and I just wanted to concentrate on coding and not infrastructure. This project also requires less than 14Gb ram / 4vCPU to run efficiently as it is only a demo and as a general rule if an application requires less power than that it should be an app service if there are no other more important concerns. This lightweight application has no need for high performance compute and will be cheaper to host on an app service plan. If this was a legacy application that had compatibility concerns, a production application that required higher performance, needed a high degree of environmental customization or may need to be ported to a different platform in the future I would think of using a VM but in this case I chose an app service for its simplicity and cost.

