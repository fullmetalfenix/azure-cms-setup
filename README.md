# azure-cms-setup


![Login](https://github.com/fullmetalfenix/azure-cms-setup/blob/main/imgs/MSAL-Quick.gif)


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
