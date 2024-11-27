### Q001
**You have two Hyper-V hosts named Host1 and Host2.
Host1 has an Azure virtual machine named VM1 that was deployed by using a custom Azure Resource
Manager template.  
You need to move VM1 to Host2. What should you do?**

- From the Update management blade, click Enable.
- From the Overview blade, move VM1 to a different subscription.
- [From the Redeploy blade, click Redeploy.](#q001)
- From the Profile blade, modify the usage location.


> In Azure, if you need to move a virtual machine to a different physical host within Azure's infrastructure, the Redeploy option on the VM’s blade can be used. This action effectively moves the VM to a new physical host within the same region, which can help resolve issues related to the VM's current host.
>
> However, if the requirement is to move the VM from one on-premises Hyper-V host to another (e.g., Host1 to Host2), this would not be directly achievable through the Azure portal options listed, as Azure doesn’t control on-premises Hyper-V environments. For on-premises Hyper-V migrations, you'd typically use Hyper-V Manager or System Center Virtual Machine Manager (SCVMM) tools to perform such a move. If this question is interpreted strictly as an Azure operation, Redeploy is the closest match, though this would only apply within Azure's infrastructure and not across on-premises Hyper-V hosts.
>
> **Hyper-V** is Microsoft’s virtualization platform, enabling users to create and manage virtual machines (VMs). Originally built for on-premises Windows Server environments, Hyper-V allows multiple virtual machines to run on a single physical server. Each VM operates independently and has its own operating system and applications, sharing physical resources like CPU, memory, and storage of the host.
>
> **Blades** are part of the Azure portal's graphical user interface (GUI), designed to organize settings, resources, and tools for each Azure service in a way that's intuitive and easy to navigate.
>

- https://chatgpt.com/share/672c3f12-52b4-8000-b666-e06c5a811e96
- https://learn.microsoft.com/en-us/troubleshoot/azure/virtual-machines/windows/redeploy-to-new-node-windows#use-the-azure-portal

---

### Q002
**You have downloaded an Azure Resource Manager template to deploy numerous virtual machines. The template is based on a current virtual machine, but must be adapted to reference an administrative password.  
You need to make sure that the password is not stored in plain text.  
You are preparing to create the necessary components to achieve your goal.  
Which of the following should you create to achieve your goal?**

- [An Azure Key Vault](#q002)
- An Azure Storage account
- Azure Active Directory (AD)
- Identity Protection
- [An access policy](#q002)
- An Azure policy
- A backup policy

> **An Azure Key Vault:** Azure Key Vault is designed to securely store secrets such as passwords, keys, and certificates. By storing the administrative password in Key Vault, you can securely reference it in your template without exposing it in plain text.
>
> **An access policy:** In Azure Key Vault, access policies are used to control permissions for users or applications that need access to the secrets. By creating an access policy, you can grant the ARM template deployment the necessary permissions to retrieve the password from Key Vault.

- https://chatgpt.com/share/672c4b4e-1600-8000-b231-2d5e553e04c3
- https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/key-vault-parameter?tabs=azure-cli

---

### Q003
**Your company has an Azure Kubernetes Service (AKS) cluster that you manage from an Azure AD-joined device. The cluster is located in a resource group.  
Developers have created an application named MyApp. MyApp was packaged into a container image.
You need to deploy the YAML manifest file for the application.  
Solution: You install the Azure CLI on the device and run the `kubectl apply -f myapp.yaml` command.  
Does this meet the goal?**

- [Yes](#q003)
- No

> This solution meets the goal. By installing the Azure CLI on your Azure AD-joined device, you can access the AKS cluster, provided you are authenticated correctly. The `kubectl apply -f myapp.yaml` command will deploy the application described in the myapp.yaml file to the AKS cluster.
>
> The solution provided involves using kubectl, which is the Kubernetes command-line tool, to apply the YAML manifest file (myapp.yaml) for deploying the application. Since you're managing the AKS cluster from an Azure AD-joined device and have the Azure CLI installed, running `kubectl apply -f myapp.yaml` command will deploy the application to the AKS cluster. This is a common and valid method for deploying applications to Kubernetes clusters, including AKS. Therefore, option A is correct.

- https://chatgpt.com/share/672c54e0-1194-8000-8c3c-353ecdde786a

---

### Q004
**Your company has an Azure Kubernetes Service (AKS) cluster that you manage from an Azure AD-joined device. The cluster is located in a resource group.
Developers have created an application named MyApp. MyApp was packaged into a container image.
You need to deploy the YAML manifest file for the application.  
Solution: You install the docker client on the device and run the `docker run -it microsoft/azure-cli:0.10.17` command.  
Does this meet the goal?**

- Yes
- [No](#q004)
  
> Installing the Docker client and running the `docker run -it microsoft/azure-cli:0.10.17` command will start an interactive Azure CLI session within a Docker container, but it does not directly deploy the YAML manifest file to the AKS cluster. To deploy the YAML manifest file, you need to use the `kubectl apply -f myapp.yaml` command, which is specifically designed for interacting with Kubernetes clusters

- https://chatgpt.com/share/672c67ab-cb3c-8000-89fb-a4b4e08f9d4d

---

### Q005
**Your company has a web app named WebApp1.
You use the WebJobs SDK to design a triggered App Service background task that automatically invokes a function in the code every time new data is received in a queue.  
You are preparing to configure the service processes a queue data item.  
Which of the following is the service you should use?**

- Logic Apps
- [WebJobs](#q005)
- Flow
- Functions

> The WebJobs SDK is specifically designed to run background tasks within an Azure Web App. It allows you to create triggered functions that respond to events such as new data in a queue. This makes it the appropriate service for processing queue data items in your scenario.  All app service plans support WebJobs. There's no extra cost to use WebJobs.

- https://chatgpt.com/share/672c6a15-d284-8000-8b7a-3e96fa5c6558

---

### Q006
**Your company has an Azure subscription. You need to deploy a number of Azure virtual machines to the subscription by using Azure Resource Manager (ARM) templates.The virtual machines will be included in a single availability set.  
You need to ensure that the ARM template allows for as many virtual machines as possible to remain accessible in the event of fabric failure or maintenance.  
Which of the following is the value that you should configure for the `platformFaultDomainCount` property?**

- 10
- 30
- Min Value
- [Max Value](#q006)

> The `platformFaultDomainCount` property defines the number of fault domains for an availability set in Azure. A fault domain is essentially a logical group of underlying hardware that shares a single point of failure (such as a physical server or rack). To maximize the number of virtual machines that can remain accessible during a fabric failure or maintenance, you would configure the `platformFaultDomainCount` to the **maximum value** supported by Azure.
>
> Azure provides a **maximum of 3 fault domains** for an availability set by default, though this can be extended based on the region and the specific deployment architecture. You can set the parameter `--platform-fault-domain-count` to 1, 2, or 3 (default of 3 if not specified).

- https://chatgpt.com/share/672c6c5f-d6d4-8000-91c1-b518862e67c2
- https://learn.microsoft.com/en-us/azure/virtual-machine-scale-sets/virtual-machine-scale-sets-manage-fault-domains

---

### Q007
**Your company has an Azure subscription.
You need to deploy a number of Azure virtual machines to the subscription by using Azure Resource Manager (ARM) templates. The virtual machines will be included in a single availability set.  
You need to ensure that the ARM template allows for as many virtual machines as possible to remain accessible in the event of fabric failure or maintenance.  
Which of the following is the value that you should configure for the `platformUpdateDomainCount` property?**

- 10
- [20](#q007)
- 30
- 40

> Update domains indicate groups of virtual machines and underlying physical hardware that can be rebooted at the same time. By configuring the `platformUpdateDomainCount` property to the **maximum value (20)**, you ensure that the virtual machines are spread across as many update domains as possible. This helps to minimize the impact of maintenance events on the availability of the virtual machines.
>
> An **Availability Set** is a logical grouping of VMs in Azure that helps to keep your application available during planned maintenance or hardware failures. When VMs are placed in an availability set, they are distributed across multiple **fault domains** and **update domains**. This configuration is essential for ensuring high availability of applications by minimizing the chance of simultaneous failures across multiple VMs.
>
> A **Fault Domain** is a group of hardware that shares a common power source and network switch. Placing VMs in different fault domains protects your application from potential failures at the physical hardware level. For example:
>- **Physical isolation:** VMs placed in different fault domains run on separate physical racks, so if one rack experiences an outage (due to power or network failure), VMs in other fault domains remain unaffected.
>- **Default setup:** Azure provides two or three fault domains within an availability set, depending on the region.
>
> **Example:** If an application has three VMs spread across three fault domains, a failure in one fault domain will only affect one VM, and the other two VMs will continue to run, ensuring partial service continuity.
>
> An **Update Domain** is a group of VMs that can undergo maintenance (such as patching or hardware updates) at the same time. During planned maintenance events, Azure sequentially updates one update domain at a time to maintain high availability.
>- **Logical grouping:** VMs within an availability set are distributed across multiple update domains so that maintenance on one update domain doesn't impact VMs in other update domains.
>- **Configurable count:** By default, Azure uses up to five update domains for availability sets, but this can be increased to a maximum of 20 for larger applications.
>
> **Example:** If an availability set has three update domains with one VM per domain, Azure will update one domain at a time. During an update, only one VM is temporarily taken offline, while the other VMs continue to serve the application.

- https://chatgpt.com/share/672c861d-020c-8000-82c2-28737417bf1f

---

### Q008
**You are creating an Azure Cosmos DB account that makes use of the SQL API. Data will be added to the account every day by a web application.  
You need to ensure that an email notification is sent when information is received from IoT devices, and that compute cost is reduced.  
You decide to deploy a function app. Which of the following should you configure the function app to use?**

- Azure Cosmos DB connector
- SendGrid action
- [Consumption plan](#q008)
- Azure Event Hubs binding
- [SendGrid binding](#q008)

> **Consumption plan** - This plan ensures that you only pay for the function app execution time, making it cost-effective, especially for event-driven applications with sporadic traffic.
>
> **SendGrid binding** - This binding can be used to send email notifications directly from the function app when specific events occur, such as the reception of IoT data.
>
> **CosmosDB Connectors** are only for Logic Apps, and other **CosmosDB triggers** aren't part of the options. That's what makes this problem tricky and unrealistic.

- https://chatgpt.com/share/672c8a69-f354-8000-a9a8-2ef308b7deb0

---

### Q009
**This question requires that you evaluate the underlined text to determine if it is correct.  
Your company has an on-premises deployment of MongoDB, and an Azure Cosmos DB account that makes use of the MongoDB API. You need to devise a strategy to migrate MongoDB to the Azure Cosmos DB account.  
<u>You include the Data Management Gateway tool in your migration strategy.</u>  
Instructions: Review the underlined text. If it makes the statement correct, select "No change required." If the statement is incorrect, select the answer choice that makes the statement correct.**

- No change required
- [mongorestore](#q009)
- Azure Storage Explorer
- AzCopy
  
> The **Data Management Gateway** tool is a client agent that you must install in your on-premises environment to copy data between cloud and on-premises data stores, but not used for migrating MongoDB data to Azure Cosmos DB. Instead, **mongorestore** is commonly used to restore MongoDB data from a backup into another MongoDB-compatible service, such as an Azure Cosmos DB account using the MongoDB API.
>
> Here's a quick overview of each tool in the context of MongoDB migration:
>- **Data Management Gateway:** Used for hybrid data integration in services like Azure Data Factory, not suitable for direct MongoDB migration.
>- **mongorestore:** A tool specifically for MongoDB that restores data from a backup created by the mongodump tool, making it the appropriate choice for migrating data to Cosmos DB.
>- **Azure Storage Explorer:** Useful for managing Azure Storage resources but not designed for MongoDB data migration.
>- **AzCopy:** Used for transferring data to and from Azure Storage accounts; it's not intended for MongoDB migrations.

- https://chatgpt.com/share/672c8d19-2440-8000-840c-97650b97264f

---

### Q010
**You are developing an e-Commerce Web App.  
You want to use Azure Key Vault to ensure that sign-ins to the e-Commerce Web App are secured by using Azure App Service authentication and Azure Active
Directory (AAD).  
What should you do on the e-Commerce Web App?**

- Run the az keyvault secret command.
- Enable Azure AD Connect.
- [Enable Managed Service Identity (MSI).](#q010)
- Create an Azure AD service principal.

> **Managed Service Identity (MSI)** is a feature in Azure that allows you to securely authenticate an Azure service to other Azure services without having to manage credentials. By enabling MSI on the Azure App Service hosting the e-Commerce Web App, you can create a trust relationship between the App Service and Azure Key Vault. This allows the e-Commerce Web App to authenticate with Azure Active Directory (AAD) and securely retrieve secrets from the Key Vault.
>
> Explanation of Other Options:
>- **Run the az keyvault secret command:** This command is used to manage secrets within Azure Key Vault but does not directly relate to securing sign-ins with AAD.
>- **Enable Azure AD Connect:** Azure AD Connect is for synchronizing on-premises directories with Azure AD and is not required to secure an App Service Web App.
>- **Create an Azure AD service principal:** While service principals can enable applications to access Azure resources, using MSI is preferred because it manages credentials automatically and provides enhanced security.

- https://chatgpt.com/share/672c8ea4-8ba8-8000-9c22-2ce0caed7f03

---

### Q011
**This question requires that you evaluate the underlined text to determine if it is correct.  
Your Azure Active Directory (Azure AD) tenant has an Azure subscription linked to it. Your developer has created a mobile application that obtains Azure AD access tokens using the OAuth 2 implicit grant type.
The mobile application must be registered in Azure AD.  
<u>You require a redirect URI from the developer for registration purposes.</u>  
Instructions: Review the underlined text. If it makes the statement correct, select "No change required." If the statement is incorrect, select the answer choice that makes the statement correct.**

- [No change required.](#q011)
- a secret
- a login hint
- a client ID

> When registering an application in Azure AD, a **redirect URI** is required to specify where the authorization server should redirect users after they have authenticated. This is especially necessary when using the OAuth 2.0 implicit grant flow, as it helps ensure that the tokens are sent to the correct URI specified by the developer.
> 
> **Secret** is not applicable here because the implicit grant type does not require a client secret, as it's often used in client-side applications where storing secrets securely is challenging.
> 
> **Login hint** is an optional parameter that can be used to pre-fill a user's email during authentication, but it's not necessary for registration.
> 
> **Client ID** is also required for registration but is provided by Azure AD upon app registration, not by the developer.

- https://chatgpt.com/share/672c94ef-749c-8000-b9ee-6f7e0a0f9310

---

### Q012
**You are creating an Azure key vault using PowerShell. Objects deleted from the key vault must be kept for a set period of 90 days.  
Which two of the following parameters must be used in conjunction to meet the requirement? (Choose two.)**

- EnabledForDeployment
- [EnablePurgeProtection](#q012)
- EnabledForTemplateDeployment
- [EnableSoftDelete](#q012)

>**EnableSoftDelete:** Ensures that deleted objects are retained in a "soft delete" state, allowing recovery within a retention period (typically 90 days).
>**EnablePurgeProtection:** Prevents permanent deletion (purge) of "soft deleted" objects, enforcing retention for the specified period.

- https://chatgpt.com/share/672c9851-0024-8000-8844-e28689201c67

---

### Q013
**You have an Azure Active Directory (Azure AD) tenant.  
You want to implement multi-factor authentication by making use of a conditional access policy. The conditional access policy must be applied to all users when they access the Azure portal.  
Which three settings should you configure?**

- Assignments
    - [Users and groups](#q013)
    - [Cloud apps](#q013)
    - Conditions
- Access controls
    - [Grant](#q013)
    - Session 


>**Assignments > Users and groups**  
>Select all users or specify groups that you want the policy to apply to. In this case, you want to apply it to all users.
>
>**Assignments > Cloud apps**  
>Select the specific application to which the policy applies. For enforcing MFA when accessing the Azure portal, select the "Microsoft Azure Management" application.
>
>**Access controls > Grant**  
>Choose the "Grant" control and select "Require multi-factor authentication" to enforce MFA as a requirement for accessing the Azure portal.

- https://chatgpt.com/share/672c9a33-6728-8000-99bd-68c104f88be9
- https://learn.microsoft.com/en-us/entra/identity/authentication/tutorial-enable-azure-mfa

---

### Q014
**You manage an Azure SQL database that allows for Azure AD authentication.  
You need to make sure that database developers can connect to the SQL database via Microsoft SQL Server Management Studio (SSMS). You also need to make sure the developers use their on-premises Active Directory account for authentication. Your strategy should allow for authentication prompts to be kept to a minimum.  
Which of the following should you implement?**

- Azure AD token.
- Azure Multi-Factor authentication.
- [Active Directory integrated authentication.](#q014)
- OATH software tokens.

> Active Directory integrated authentication is the correct option as it allows users to connect to the database using their Windows credentials, which are authenticated through their on-premises Active Directory. This option avoids the need for users to enter their credentials each time they connect to the database, reducing authentication prompts to a minimum.

- https://chatgpt.com/share/672c9e5e-f3c4-8000-b175-35879d41d8f1

---

### Q015
**You are developing an application to transfer data between on-premises file servers and Azure Blob storage. The application stores keys, secrets, and certificates in Azure Key Vault and makes use of the Azure Key Vault APIs.   
You want to configure the application to allow recovery of an accidental deletion of the key vault or key vault objects for 90 days after deletion.   
What should you do?**

- Run the `Add-AzKeyVaultKey` cmdlet.
- [Run the `az keyvault update --enable-soft-delete true --enable-purge-protection true` CLI.](#q015)
- Implement virtual network service endpoints for Azure Key Vault.
- Run the `az keyvault update --enable-soft-delete false` CLI.

> To allow the recovery of an accidental deletion of the Key Vault or its objects for 90 days after deletion, you need to enable soft delete and purge protection.  
>- **Soft delete** ensures that deleted keys, secrets, and certificates are retained for a specified retention period (90 days by default) and can be recovered during that time.  
>- **Purge protection** prevents the permanent deletion (purging) of the Key Vault or its objects during the retention period. It ensures that even if an object is deleted, it cannot be permanently purged until the retention period expires.

- https://chatgpt.com/share/672ca021-be14-8000-9e7a-37888bee45d8
  
---

### Q016
**You have developed a Web App for your company. The Web App provides services and must run in multiple regions.  
You want to be notified whenever the Web App uses more than 85 percent of the available CPU cores over a 5 minute period. Your solution must minimize costs.  
Which command should you use?**

```
az monitor metrics alert create -n myAlert -g myResourceGroup
--scopes targetResourceID
--condition "SLOT_1 > 85"
SLOT_2 5m

```

- SLOT_1
    - CPU Usage
    - Percentage CPU
    - [avg Percentage CPU](#q016)
- SLOT_2
    - [--window-size](#q016)
    - --evaluation-frequency
    - --auto-mitigate

> **Window size** is the period of time over which Azure Monitor will collect metrics for a metric alert rule.  
> **Evaluation frequency** is the frequency with which Azure Monitor will evaluate the metric alert rule for violations.  
> 
> if you set the window size to 5 minutes and the evaluation frequency to 1 minute (default), Azure Monitor will collect metrics for the previous 5 minutes and then evaluate the metric alert rule for violations every minute. This means that if there is a violation in the 5 minute window, Azure Monitor will detect it within 1 minute. We want to get percent “over a 5 minute period”, we have to use window size parameter. Only use evaluation frequency parameter is not enough for getting question request.
> 
> For anyone wondering why it's `--window-size` and not `--evaluation-frequency`: you want the average across 5 minutes. With `--evaluation-frequency` you don't go for averages, you simply check what the given value is at specific intervals.

- https://chatgpt.com/share/672ca33a-40a4-8000-ae54-bfe5b72c0d18
- https://docs.microsoft.com/en-us/cli/azure/monitor/metrics/alert

---

### Q017
**You are configuring a web app that delivers streaming video to users. The application makes use of continuous integration and deployment.  
You need to ensure that the application is highly available and that the users' streaming experience is constant. You also want to configure the application to store data in a geographic location that is nearest to the user.  
Solution: You include the use of Azure Redis Cache in your design.   
Does the solution meet the goal?**

- Yes
- [No](#q017)

> Azure Redis Cache can be helpful in improving the performance of the application by caching frequently accessed data, such as session states or metadata, but it does not address the need for high availability and geographic data storage for streaming video. Azure Redis Cache is not designed for storing or delivering large-scale video content.  
> 
> To meet the goal, a combination of **Azure Blob Storage**, **Azure CDN**, and possibly **Azure Front Door** for global load balancing would be more appropriate.

- https://chatgpt.com/share/672cb53f-0d94-8000-b0a0-e5384ad0ca10

---

### Q018
**You are configuring a web app that delivers streaming video to users. The application makes use of continuous integration and deployment.  
You need to ensure that the application is highly available and that the users' streaming experience is constant. You also want to configure the application to store data in a geographic location that is nearest to the user.  
Solution: You include the use of an Azure Content Delivery Network (CDN) in your design.  
Does the solution meet the goal?**

- [Yes](#q018)
- No

> Using an Azure Content Delivery Network (CDN) is a valid solution for delivering streaming video to users with high availability and performance. The CDN caches and distributes content globally from edge locations, ensuring that users receive content from the nearest geographic location, thus improving the streaming experience. This design also supports highly available content delivery, which is critical for applications relying on continuous integration and deployment for scalability.
>
> Additionally, the use of a CDN can help offload traffic from the origin server, reducing latency and providing a constant streaming experience to users.

- https://chatgpt.com/share/672cb643-31ec-8000-9796-265310b64f7d
  
---

### Q019
**You are configuring a web app that delivers streaming video to users. The application makes use of continuous integration and deployment.  
You need to ensure that the application is highly available and that the users' streaming experience is constant. You also want to configure the application to store data in a geographic location that is nearest to the user.  
Solution: You include the use of a Storage Area Network (SAN) in your design.  
Does the solution meet the goal?**

- Yes
- [No](#q019)

>A **Storage Area Network (SAN)** is typically used for high-performance block-level storage for enterprise applications and is often more suited to applications that require fast, low-latency access to a shared storage infrastructure. It does not address the need for high availability and geographic proximity to users in the context of streaming video.
>
>To meet the goal, you should consider using **Azure Blob Storage** or **Azure Content Delivery Network (CDN)**, which can cache the streaming content closer to the users' geographic locations. These services provide scalability, high availability, and the ability to deliver content to users with lower latency.

- https://chatgpt.com/share/672cb73a-93e4-8000-b6d0-9d9999e20f0b

---

### Q020
**You develop a Web App on a tier D1 app service plan.  
You notice that page load times increase during periods of peak traffic.  
You want to implement automatic scaling when CPU load is above 80 percent. Your solution must minimize costs.  
What should you do first?**

- Enable autoscaling on the Web App.
- Switch to the Premium App Service tier plan.
- [Switch to the Standard App Service tier plan.](#q020)
- Switch to the Azure App Services consumption plan.

> Tier D1 is a basically **shared** app service plan, so we need to move **standard** or **premium** plan to enable auto scaling. As we need to provide low cost solution, then standard plan will be best for this approach.  
> The **consumption** plan is invalid as it is only applicable for the Azure Function app, not for a web app.

- https://chatgpt.com/share/672cb8a2-3fe8-8000-a9e0-e8389f30488e

---

### Q021
**Your company's Azure subscription includes an Azure Log Analytics workspace.  
Your company has a hundred on-premises servers that run either Windows Server 2012 R2 or Windows Server 2016, and is linked to the Azure Log Analytics workspace. The Azure Log Analytics workspace is set up to gather performance counters associated with security from these linked servers.  
You must configure alerts based on the information gathered by the Azure Log Analytics workspace.
You have to make sure that alert rules allow for dimensions, and that alert creation time should be kept to a minimum. Furthermore, a single alert notification must be created when the alert is created and when the alert is resolved.  
You need to make use of the necessary signal type when creating the alert rules.  
Which of the following is the option you should use?**

- The Activity log signal type.
- The Application Log signal type.
- [The Metric signal type.](#q021)
- The Audit Log signal type.

> The Metric signal type is the correct option for creating alert rules based on performance counters associated with security gathered by the Azure Log Analytics workspace. The Metric signal type allows you to create alerts based on metrics collected by Azure Monitor. This includes metrics collected by Log Analytics from your servers, such as performance counters associated with security. The Metric signal type allows you to set dimensions, which can be used to filter the metrics and reduce the noise of alerts. You can also configure the alert to be fired on multiple criteria and the alert creation time is kept to a minimum. Furthermore, Metric Alerts are stateful - only notifying once when alert is fired and once when alert is resolved; as opposed to Log alerts, which are stateless and keep firing at every interval if the alert condition is met.
>
> **Activity log** and **Audit log** signal types are more suited for auditing and operational events, not performance counters.
> **Application Log** is used for application-specific logs rather than system performance counters.

- https://chatgpt.com/share/672d04ef-d598-8000-88e9-dcfc0808cf82
- https://learn.microsoft.com/en-us/azure/azure-monitor/alerts/alerts-overview

---

### Q022
**You are developing a solution for a public facing API.  
The API back end is hosted in an Azure App Service instance. You have implemented a RESTful service for the API back end.  
You must configure back-end authentication for the API Management service instance.  
Solution: You configure Basic gateway credentials for the Azure resource.  
Does the solution meet the goal?**

- Yes
- [No](#q022)
  
> Configuring Basic gateway credentials is not recommended for securing a public-facing API because it involves sending credentials (username and password) with each request. This method can expose security vulnerabilities, as credentials are transmitted in an easily readable format. It's better to use more secure methods like API keys, OAuth tokens, or other authentication mechanisms for better protection in a public API scenario
>
> The App Service doesn't support basic-auth at all; though APIM does. The tricky part is the word "resource" which is App Service.

- https://learn.microsoft.com/en-us/azure/api-management/authentication-basic-policy

---

### Q023
**You are developing a solution for a public facing API.  
The API back end is hosted in an Azure App Service instance. You have implemented a RESTful service for the API back end.  
You must configure back-end authentication for the API Management service instance.  
Solution: You configure Client cert gateway credentials for the HTTP(s) endpoint.  
Does the solution meet the goal?**

- [Yes](#q023)
- No

> If backend is accepts HTTP(S) Then Basic AUTH or Certificate will work. So, Client Certificate + HTTP(s) will work.
>
> APIM supports both, but that is only part of the question.  
Does App Service itself support basic auth? NO not really (only a hacky way).  
Does app Service Support certificate auth? YES, built in the Azure portal directly as a setting for app Service.

- https://learn.microsoft.com/en-us/azure/api-management/authentication-certificate-policy

---

### Q024
**You are developing a solution for a public facing API.  
The API back end is hosted in an Azure App Service instance. You have implemented a RESTful service for the API back end.  
You must configure back-end authentication for the API Management service instance.  
Solution: You configure Basic gateway credentials for the HTTP(s) endpoint.  
Does the solution meet the goal?**

- [Yes](#q024)
- No
  
> If backend is accepts HTTP(S) Then Basic AUTH or Certificate will work. So Basic + HTTPS will work. 
> Configuring Basic gateway credentials for the HTTP(s) endpoint is a valid solution for back-end authentication in API Management. Basic authentication involves sending a username and password with each request.

---

### Q025
**You are developing a solution for a public facing API.  
The API back end is hosted in an Azure App Service instance. You have implemented a RESTful service for the API back end.  
You must configure back-end authentication for the API Management service instance.  
Solution: You configure Client cert gateway credentials for the Azure resource.  
Does the solution meet the goal?**

- [Yes](#q025)
- No
  
> If backend is accepts HTTP(S) Then Basic AUTH or Certificate will work. So Client Certificate + HTTP(s) will work.

---

### Q026
**You are developing an application that applies a set of governance policies for internal and external services, as well as for applications.  
You develop a stateful ASP.NET Core 2.1 web application named PolicyApp and deploy it to an Azure App Service Web App.  
The PolicyApp reacts to events from Azure Event Grid and performs policy actions based on those events.  
You have the following requirements:  
• Authentication events must be used to monitor users when they sign in and sign out.  
• All authentication events must be processed by PolicyApp.  
• Sign outs must be processed as fast as possible.  
What should you do?**

- Create a new Azure Event Grid subscription for all authentication events. Use the subscription to process sign-out events.
- Create a separate Azure Event Grid handler for sign-in and sign-out events.
- Create separate Azure Event Grid topics and subscriptions for sign-in and sign-out events.
- [Add a subject prefix to sign-out events. Create an Azure Event Grid subscription. Configure the subscription to use the subjectBeginsWith filter.](#q026)

> **Subject Prefix:** Adding a subject prefix to sign-out events allows you to distinguish between sign-in and sign-out events.  
> **Efficient Filtering:** Using the `subjectBeginsWith` filter on the Event Grid subscription ensures that only sign-out events are filtered and processed by PolicyApp immediately, which aligns with the requirement to handle sign-outs as quickly as possible.  
> **Optimized Event Processing:** By filtering on specific events, PolicyApp can focus on processing sign-outs without delay, while still receiving all other authentication events for monitoring.
>
> **Why the Other Options Are Less Suitable:**  
> **Option A:** A single subscription for all authentication events would not optimize for quick processing of sign-outs, as PolicyApp would need to handle all events without specific filtering.  
> **Option B:** Creating separate handlers for sign-in and sign-out events could add complexity without providing a direct mechanism for prioritizing sign-out events.  
> **Option C:** Creating separate topics would add overhead and is unnecessary for this scenario, as the subject prefix and filter can handle event differentiation within the same topic.

- https://chatgpt.com/share/672d8fa3-cfd4-8000-a6e6-cda52f5f4007
- https://learn.microsoft.com/en-us/azure/event-grid/concepts
- https://learn.microsoft.com/en-us/azure/event-grid/event-filtering

---

### Q027
**You are developing a C++ application that compiles to a native application named process.exe  
The application accepts images as input and returns images in one of the following image  
formats: GIF, PNG, or JPEG.  
You must deploy the application as an Azure Function.  
You need to configure the function and host json files.  
How should you complete the json files?**

```
//function.json
{
    SLOT_1,
    "direction": "out",
    "name": "result"
}

//host.json
{
    SLOT_2,
    {
        "defaultExecutablePath": "process.exe"
    },
    SLOT_3
}

```

- SLOT_1
    - ["type": "http"](q027)
    - "platform": "gem"
    - "datatype" : "stream"
    - "path": "process.exe"
- SLOT_2
    - ["customHandler": { "description":](#q027)
    - "languageWorker" : { "path" : 
    - "extensions" : {"worker" : 
    - "extensionBundle" : 
- SLOT_3
    - "enableForwardingHttpRequest": true
    - ["enableForwardingHttpRequest": false](#q027)


> To configure the JSON files for deploying a native C++ application in Azure Functions, we'll use a custom handler to invoke the `process.exe` executable. This setup enables Azure Functions to handle custom runtimes like C++ by calling a specific executable.
>
> **SLOT_1** should define the type as `http`, which specifies that the function will handle HTTP requests. This allows the function to receive image data via HTTP.
>
> **SLOT_2** requires a `customHandler` configuration with a description, setting up the function to use a custom handler rather than a predefined Azure Functions runtime.
>
> **SLOT_3** should be set to `enableForwardingHttpRequest: true`, which enables the function to forward HTTP requests to the custom handler.
>
```json
// function.json
{
    "type": "http",
    "direction": "out",
    "name": "result"
}

// host.json
{
    "customHandler": {
        "description": {
            "defaultExecutablePath": "process.exe"
        }
    },
    "enableForwardingHttpRequest": true
}

```

- https://chatgpt.com/share/672d966d-f20c-8000-9db8-281d3a094afa
- https://learn.microsoft.com/en-us/azure/azure-functions/functions-custom-handlers
  
---

### Q028
**You are developing an Azure Static Web app that contains training materials for a tools company. Each tool's training material is contained in a static web page that is linked from the tools publicly available description page.   
A user must be authenticated using Azure AD prior to viewing training.   
You need to ensure that the user can view training material pages after authentication.   
How should you complete the configuration file?**

```
{
    "SLOT_1": {
        "SLOT_2": {
            "redirect": "/.auth/login/SLOT_3?post_login_redirect_uri=SLOT_4",
            "statusCode": 302
        }
    }
}
```

- SLOT_1
    - routes
    - headers
    - [responseOverrides](#q028)
    - navigationFallback
- SLOT_2
    - 400
    - [401](#q028)
    - 403
    - 404
- SLOT_3
    - [aad](#q028)
    - azure
    - graph
    - microsoftonline
- SLOT_4
    - orig
    - route
    - return
    - [.referrer](#q028)

> **responseOverrides:** used to define custom responses for specific HTTP status codes.  
> **401:** to handle unauthorized access, redirecting users to Azure AD authentication.  
> **aad:** indicating Azure AD as the authentication provider.  
> **.referrer:** to direct users back to the page they initially requested after authentication.

```json
{
    "responseOverrides": {
        "401": {
            "redirect": "/.auth/login/aad?post_login_redirect_uri=.referrer",
            "statusCode": 302
        }
    }
}
```

- https://learn.microsoft.com/en-us/azure/static-web-apps/configuration#restrict-access-to-entire-application
- https://learn.microsoft.com/en-us/azure/static-web-apps/authentication-authorization#set-up-post-sign-in-redirect

---

### Q029
**You are authoring a set of nested Azure Resource Manager templates to deploy Azure resources. You author an Azure Resource Manager template named `mainTemplate.json` that contains the following linked templates: `linkedTemplate1.json`, `linkedTemplate2.json`.   
You add parameters to a parameters template file named `mainTemplate.parameters.json.` You save all templates on a local device in the C:  templates   folder.   
You have the following requirements:   
• Store the templates in Azure for later deployment.   
• Enable versioning of the templates.   
• Manage access to the templates by using Azure RBAC.   
• Ensure that users have read-only access to the templates.   
• Allow users to deploy the templates.   
You need to store the templates in Azure.   
How should you complete the command?**

```
az SLOT_1
--name templateStore
--version "1.0"
--resource-group templatesRG
--location "eastus"
-- template-file SLOT_2 "C:   templates  "
--tags Dept=HumanResources Environment=Production
```

- SLOT_1
    - [ts create](#q029)
    - storage account create
    - storage account update
    - blueprint artifact template create
- SLOT_2
    - [mainTemplate.json](#q029)
    - linkedTemplate1.json
    - linkedTemplate2.json
    - mainTemplate.parameters.json
  
> To store ARM templates in Azure with versioning, access control, and the ability to deploy them later, we should use **Azure Template Specs**. This provides version control, integrates with Azure RBAC for access management, and allows read-only access for deployment purposes.
>
> For **SLOT_1**, the correct command is `ts create`, as it is used to create a Template Spec in Azure.  
> For **SLOT_2**, specify `mainTemplate.json`, the main file containing links to other templates.

- https://chatgpt.com/share/672da70c-f99c-8000-9ac9-0d8fd222cfc8
- https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/template-specs-create-linked?tabs=azure-cli#create-template-spec
  
---

### Q030
**You are developing a service where customers can report news events from a browser using Azure Web PubSub. The service is implemented as an Azure Function App that uses the JSON WebSocket subprotocol to receive news events.   
You need to implement the bindings for the Azure Function App.   
How should you configure the binding?**

```
{
    "bindings":[
        {
            "type": "SLOT_1",
            "direction": "in",
            "name": "data",
            "eventName": "message",
            "eventType": "SLOT_2"
        }
    ]
}
```

- SLOT_1
    - user
    - system
    - message
    - connected
    - [webPubSub Trigger](#q030)
    - webPub Sub Connection
- SLOT_2
    - [user](#q030)
    - system
    - message
    - connected
    - webPubSub Trigger
    - webPub Sub Connection

> EventType can be either `user` or `system`. EventType says who triggers the function. The question says: 'where **customers** can report news events from a browser using Azure Web PubSub'. For me customer is a person, not a system. So the answer is user.  
>
> you can be sure that type is user. `"eventName":"message"` can only be for `"eventType":"user"`.

- https://learn.microsoft.com/en-us/azure/azure-web-pubsub/reference-functions-bindings?tabs=javascript-v3

---

### Q031
**You are building a software-as-a-service (SaaS) application that analyzes DNA data that will run on Azure virtual machines (VMs) in an availability zone. The data is stored on managed disks attached to the VM. The performance of the analysis is determined by the speed of the disk attached to the VM.   
You have the following requirements:   
• The application must be able to quickly revert to the previous day's data if a systemic error is detected.   
• The application must minimize downtime in the case of an Azure datacenter outage.   
You need to provision the managed disk for the VM to maximize performance while meeting the requirements.   
Which type of Azure Managed Disk should you use?**

**Requirement:**
- Disk type
    - [Premium SSD](#q031)
    - Standard SSD
    - Standard HDD
- Redundancy
    - Geo-redundant storage (GRS)
    - [Zone-redundant storage (ZRS)](#q031)
    - Locally-redundant storage (LRS)

> They are asking for high performance workloads which is supported by Premium tier.  
> Also they are asking for zone redundancy (if datacenter goes down, NOT region outage). Also managed disk doesn't support GRS.
>
> Azure Disk Backup supports multiple types of Managed Disks, including Standard HDD, Standard SSD, and Premium SSD1. However, Premium SSDs are often preferred for their superior performance and reliability, which is crucial for your DNA analysis application.

- https://chatgpt.com/share/672dadd4-8e34-8000-9e96-2b0bab6a3c9a
- https://learn.microsoft.com/en-us/azure/virtual-machines/disks-types
- https://learn.microsoft.com/en-us/azure/virtual-machines/disks-redundancy
  
---

### Q032
**You are developing an application that includes two Docker containers.   
The application must meet the following requirements:   
• The containers must not run as root.   
• The containers must be deployed to Azure Container Instances by using a YAML file.   
• The containers must share a lifecycle, resources, local network, and storage volume.   
• The storage volume must persist through container crashes.   
• The storage volume must be deployed on stop or restart of the containers.   
You need to configure Azure Container Instances for the application.   
Which configuration values should you use?**

**Configuration Settings:**
- Shared Lifecycle
    - [Container group](#q032)
    - Container image
    - Service endpoint
    - Resource group
- Storage volume
    - Azure file share
    - secret
    - [Empty directory](#q032)
    - Cloned git repo

> **Container group** is the only logical answer that can have shared lifecycle  
> 
> **Azure files** need root permission  
> **Secret** is for secrets and read-only  
> **EmtyDir** can persist through crash and redeployed on stop and restart. Containers that are restarted, however, aren't guaranteed to persist the data in an emptyDir volume.    
> **Cloned Git Repo** also does the job but it needs more details like Git URL and stuff which are not mentioned to be available in the question also, This mount is read-only, so while the files can be accessed, the container cannot make changes to the repository itself.

- https://chatgpt.com/share/672db52c-5750-8000-968a-be3c9c24eeba
- https://learn.microsoft.com/en-us/azure/container-instances/container-instances-container-groups?source=recommendations#what-is-a-container-group
- https://learn.microsoft.com/en-us/azure/container-instances/container-instances-volume-emptydir

---

### Q033
**You are implementing a software as a service (SaaS) ASP.NET Core web service that will run as an Azure Web App. The web service will use an on-premises SQL Server database for storage. The web service also includes a WebJob that processes data updates. Four customers will use the web service.   
• Each instance of the WebJob processes data for a single customer and must run as a singleton instance.   
• Each deployment must be tested by using deployment slots prior to serving production data.   
• Azure costs must be minimized.   
• Azure resources must be located in an isolated network.   
You need to configure the App Service plan for the Web App.   
How should you configure the App Service plan?**

**App service plan settings:**
- No. of VM instances
    - 2
    - [4](#q033)
    - 8
    - 16

- Pricing tier
    - [Isolated](#q033)
    - Standard
    - Premium
    - Consumption

> **Number of VM instances**: Since you have four customers, each with a separate instance of the WebJob that must run as a singleton instance, you need at least four instances of the App Service plan to ensure that each customer's WebJob runs independently. Therefore, you should configure the number of VM instances to be at least four.
>
> **Pricing tier**: Given the requirement for an isolated network and the need to minimize costs, the appropriate pricing tier for this scenario would be the "Isolated" tier. The Isolated tier provides dedicated infrastructure for your **App Service Environment (ASE)**, ensuring isolation and security. While it may have higher costs compared to the Standard or Premium tiers, it offers the required level of isolation and network security for your scenario.

- https://chatgpt.com/share/672db959-6894-8000-8e12-41e8a741bb10

---

### Q034
**You are a developer for a software as a service (SaaS) company that uses an Azure Function to process orders. The Azure Function currently runs on an Azure Function app that is triggered by an Azure Storage queue.   
You are preparing to migrate the Azure Function to Kubernetes using Kubernetes-based Event Driven Autoscaling (KEDA).   
You need to configure Kubernetes Custom Resource Definitions (CRD) for the Azure Function.   
Which CRDs should you configure?

**Settings:**
- Azure Function Code
    - Secret
    - [Deployment](#q034)
    - ScaledObject
    - TriggerAuthentication
- Polling Interval
    - Secret
    - Deployment
    - [ScaledObject](#q034)
    - TriggerAuthentication
- Azure Storage Connection String
    - [Secret](#q034)
    - Deployment
    - ScaledObject
    - TriggerAuthentication

> **Deployment:** To deploy Azure Functions to Kubernetes use the `func kubernetes deploy` command has several attributes that directly control how our app scales, once it is deployed to Kubernetes.  
> **ScaledObject:** With `--polling-interval`, we can control the interval used by KEDA to check Azure Service Bus Queue for messages.  
> **Secret:** Store connection strings in Kubernetes Secrets.  
>
> **KEDA (Kubernetes-based Event Driven Autoscaling)** is an open-source project that allows Kubernetes to scale workloads based on external event sources, such as messages in a queue or HTTP requests. While Kubernetes natively supports scaling based on metrics like CPU and memory usage, KEDA extends this by enabling autoscaling in response to various external event sources, such as:  
>- Azure Storage Queues  
>- Azure Event Hubs  
>- RabbitMQ  
>- Kafka  
>- HTTP requests  
>- Custom metrics  
>  
>KEDA acts as a bridge between the Kubernetes Horizontal Pod Autoscaler (HPA) and event sources, allowing your application to scale up or down based on the volume of incoming events. This is particularly useful for workloads like Azure Functions that are traditionally triggered by external events.
>
> **CRDs (Custom Resource Definitions)** in Kubernetes extend its API by allowing users to create new types of resources, beyond the standard ones (such as Pods, Deployments, Services). By defining CRDs, Kubernetes can support custom resources tailored to specific use cases.  
> In the context of migrating an Azure Function to Kubernetes with KEDA, you would define:  
> - **ScaledObject** to control scaling based on queue length.  
> - **TriggerAuthentication** to store credentials securely if needed.  
> - **Deployment** to specify how the function code should be managed in Kubernetes.  
> - **Secret** to securely store any sensitive configuration, like the Azure Storage connection string.

- https://chatgpt.com/share/672dd014-cbe8-8000-8f13-964fdfa65c43

---

### Q035
**You are creating a CLI script that creates an Azure web app and related services in Azure App Service.   
You need to automatically deploy code from GitHub to the newly created web app.   
How should you complete the script?**

```
$gitrepo = "https://github.com/Contos/webapp"
$webappname = "Webapp1103"

az group create --location westeurope --name myResourceGroup
SLOT_1 --name $webappname --resource-group myResourceGroup --sku FREE
SLOT_2 --name $webappname --resource-group myResourceGroup SLOT_3
SLOT_4 source config --name $webappname --resource-group myResourceGroup SLOT_5
```

- SLOT_1
    - az webapp
    - [az appservice plan create](#q035)
    - az webapp deployment
    - az group delete
- SLOT_2
    - [az webapp](#q035)
    - az appservice plan create
    - az webapp deployment
    - az group delete
- SLOT_3
    - --repo-url $gitrepo --branch master --manual-integration
    - git clone $gitrepo
    - [--plan $webappname](#q035)
- SLOT_4
    - az webapp
    - az appservice plan create
    - [az webapp deployment](#q035)
    - az group delete
- SLOT_5
    - [--repo-url $gitrepo --branch master --manual-integration](#q035)
    - git clone $gitrepo
    - --plan $webappname

```bash
$gitrepo = "https://github.com/Contos/webapp"
$webappname = "Webapp1103"

az group create --location westeurope --name myResourceGroup
az appservice plan create --name $webappname --resource-group myResourceGroup --sku FREE
az webapp create --name $webappname --resource-group myResourceGroup --plan $webappname
az webapp deployment source config --name $webappname --resource-group myResourceGroup --repo-url $gitrepo --branch master --manual-integration

```

- https://chatgpt.com/share/672dd781-30ac-8000-9db2-4b2f6933f0d7

---

### Q036
**You develop a software as a service (SaaS) offering to manage photographs. Users upload photos to a web service which then stores the photos in Azure Storage Blob storage. The storage account type is General-purpose V2.   
When photos are uploaded, they must be processed to produce and save a mobile-friendly version of the image. The process to produce a mobile-friendly version of the image must start in less than one minute.  
You need to design the process that starts the photo processing.   
Solution: Trigger the photo processing from Blob storage events.   
Does the solution meet the goal?**

- [Yes](#q036)
- No
  
> Azure Blob Storage can emit events that can be captured by Azure Event Grid. These events can then trigger various processes or workflows. In this scenario, when a user uploads a photo to Blob Storage, an event is generated. This event can be subscribed to by an Azure Function or a Logic App, which in turn can start the process of creating a mobile-friendly version of the image.  
> This approach is efficient and can easily meet the requirement of starting the image processing in less than one minute after the photo is uploaded. Azure Event Grid is known for its low latency in delivering events, typically in the order of seconds, which aligns well with the specified requirement.

- https://chatgpt.com/share/672ddd46-7564-8000-9cd8-4136df1e8063

---

### Q037
**You develop a software as a service (SaaS) offering to manage photographs. Users upload photos to a web service which then stores the photos in Azure Storage Blob storage. The storage account type is General-purpose V2.   
When photos are uploaded, they must be processed to produce and save a mobile-friendly version of the image. The process to produce a mobile-friendly version of the image must start in less than one minute.   
You need to design the process that starts the photo processing.   
Solution: Convert the Azure Storage account to a BlockBlobStorage storage account.   
Does the solution meet the goal?**

- Yes
- [No](#q037)

> Converting the Azure Storage account to a BlockBlobStorage storage account does not meet the requirement of starting the photo processing in less than one minute. The conversion of the storage account type would not have any impact on the time it takes to start the photo processing. A different solution such as triggering the photo processing from Blob storage events or using a queue-based solution may be more appropriate to meet the requirement.

- https://chatgpt.com/share/672ddde2-a6cc-8000-9895-88df004f1649

---

### Q038
**You develop and deploy an Azure App Service API app to a Windows-hosted deployment slot named Development. You create additional deployment slots named Testing and Production. You enable auto swap on the Production deployment slot.   
You need to ensure that scripts run and resources are available before a swap operation occurs.   
Solution: Update the `web.config` file to include the `applicationInitialization` configuration element. Specify custom initialization actions to run the scripts.   
Does the solution meet the goal?**

- [Yes](#q038)
- No
  
> The `applicationInitialization` configuration element in the `web.config` file allows you to specify custom initialization actions that run before the application is ready to serve requests. This can include running scripts or ensuring that resources are available before the application is fully operational.
  
- https://learn.microsoft.com/en-us/azure/app-service/deploy-staging-slots?tabs=portal#configure-auto-swap
- https://learn.microsoft.com/en-us/azure/app-service/deploy-staging-slots?tabs=portal#specify-custom-warm-up

---

### Q039
**You develop and deploy an Azure App Service API app to a Windows-hosted deployment slot named Development. You create additional deployment slots named Testing and Production. You enable auto swap on the Production deployment slot.   
You need to ensure that scripts run and resources are available before a swap operation occurs.   
Solution: Enable auto swap for the Testing slot. Deploy the app to the Testing slot.   
Does the solution meet the goal?

- Yes
- [No](#q039)

> Enabling auto swap for the Testing slot and deploying the app to the Testing slot does not ensure that scripts run and resources are available before a swap operation occurs. Auto swap is a feature that automatically swaps the content of the source slot with the target slot after a new deployment. It does not provide a mechanism to run scripts or ensure that resources are available before the swap occurs.

- https://learn.microsoft.com/en-us/azure/app-service/deploy-staging-slots?tabs=portal#configure-auto-swap
- https://learn.microsoft.com/en-us/azure/app-service/deploy-staging-slots?tabs=portal#specify-custom-warm-up

---

### Q040
**You develop and deploy an Azure App Service API app to a Windows-hosted deployment slot named Development. You create additional deployment slots named Testing and Production. You enable auto swap on the Production deployment slot.   
You need to ensure that scripts run and resources are available before a swap operation occurs.   
Solution: Disable auto swap. Update the app with a method named statuscheck to run the scripts. Re-enable auto swap and deploy the app to the Production slot.   
Does the solution meet the goal?**

- Yes
- [No](#q040)
  
> **Auto-swap** only works after the app deployment is successful and does not give you the opportunity to run scripts or checks prior to the swap unless specific mechanisms are put in place.  
> The reason why setting up auto swap is to warm up the application to prevent downtime, so deploying to the production slot directly is killing the purpose.

- https://chatgpt.com/share/672de4f6-4cbc-8000-a8a3-81808fb7a77e
- https://learn.microsoft.com/en-us/azure/app-service/deploy-staging-slots?tabs=portal#configure-auto-swap
- https://learn.microsoft.com/en-us/azure/app-service/deploy-staging-slots?tabs=portal#specify-custom-warm-up

---

### Q041
**You are developing an Azure Web App. You configure TLS mutual authentication for the web app.   
You need to validate the client certificate in the web app. To answer, select the appropriate options in the answer area.**

**Property:**
- Client certificate location
    - [HTTP request header](#q041)
    - Client cookie
    - HTTP message body
    - URL query string
- Encoding type
    - HTML
    - URL
    - Unicode
    - [Base64](#q041)

> the client cert will be available in your app through a `base64` encoded value in the `X-ARR-ClientCert` request header. Your application can create a certificate from this value and then use it for authentication and authorization purposes in your application.   
> For ASP.NET, the client certificate is available through the `HttpRequest.ClientCertificate` property.

- https://chatgpt.com/share/672de92a-4e30-8000-b306-16afbb8d7a57
- https://learn.microsoft.com/en-us/azure/app-service/app-service-web-configure-tls-mutual-auth

---

### Q042
**You are developing a Docker/Go using Azure App Service Web App for Containers.   
You plan to run the container in an App Service on Linux. You identify a Docker container image to use.   
None of your current resource groups reside in a location that supports Linux. You must minimize the number of resource groups required.   
You need to create the application and perform an initial deployment.   
Which three Azure CLI commands should you use to develop the solution?**

- az group create
- az group update
- az webapp update
- az webapp create
- az appservice plan create
  
> Since none of your current resource groups support Linux, you'll need to create a new resource group in a location that does.  
> Here are the three commands to accomplish this:  
> `az group create --name <resource-group-name> --location <location-supporting-linux>`  
> 
> `az appservice plan create --name <app-service-plan-name> --resource-group <resource-group-name> --is-linux --sku <pricing-tier>`  
> 
> `az webapp create --name <webapp-name> --resource-group <resource-group-name> --plan <app-service-plan-name> --deployment-container-image-name <docker-image-name>`

- https://chatgpt.com/share/672e590b-ebb0-8000-871f-3405e9cdd15e

---

### Q043
**Fourth Coffee has an ASP.NET Core web app that runs in Docker. The app is mapped to the `www.fourthcoffee.com` domain.Fourth Coffee is migrating this application to Azure.   
You need to provision an App Service Web App to host this docker image and map the custom domain to the App Service web app.   
A resource group named `FourthCoffeePublicWebResourceGroup` has been created in the `WestUS` region that contains an App Service Plan named `AppServiceLinuxDockerPlan`.   
Which order should the CLI commands be used to develop the solution?**

```
az webapp config container set
--docker-custom-image-name $dockerHubContainerPath
--name $appName
--resource-group FourthCoffeePublicWebResourceGroup
```

```
az webapp config hostname add
--webapp-name $appName
--resource-group FourthCoffeePublicWebResourceGroup
--hostname $fqdn
```

```
az webapp create
--name $appName
--plan AppServiceLinuxDockerPlan
--resource-group FourthCoffeePublicWebResourceGroup
```

```
#/bin/bash
appName="FourthCoffeePublicWeb$random"
location="WestUS"
dockerHubContainerPath="FourthCoffee/publicweb:v1"
fqdn="http://www.fourthcoffee.com">www.fourthcoffee.com
```

```bash
#Step 1: initializes the necessary variables.  
#/bin/bash
appName="FourthCoffeePublicWeb$random"
location="WestUS"
dockerHubContainerPath="FourthCoffee/publicweb:v1"
fqdn="http://www.fourthcoffee.com">www.fourthcoffee.com

#Step 2: creates the Web App in the existing App Service Plan.
az webapp create   
--name $appName   
--plan AppServiceLinuxDockerPlan   
--resource-group FourthCoffeePublicWebResourceGroup

#Step 3: configures the Web App to use the specified Docker image.
az webapp config container set   
--docker-custom-image-name $dockerHubContainerPath   
--name $appName   
--resource-group FourthCoffeePublicWebResourceGroup

#Step 4: adds the custom domain to the Web App.
az webapp config hostname add   
--webapp-name $appName   
--resource-group FourthCoffeePublicWebResourceGroup   
--hostname $fqdn

```

- https://chatgpt.com/share/672e5d19-3af0-8000-8c20-4df617e53e07

---

### Q044
**You are developing a serverless Java application on Azure. You create a new Azure Key Vault to work with secrets from a new Azure Functions application.   
The application must meet the following requirements:   
• Reference the Azure Key Vault without requiring any changes to the Java code.   
• Dynamically add and remove instances of the Azure Functions host based on the number of incoming application events.   
• Ensure that instances are perpetually warm to avoid any cold starts.   
• Connect to a VNet.   
• Authentication to the Azure Key Vault instance must be removed if the Azure Function application is deleted.   
You need to grant the Azure Functions application access to the Azure Key Vault.
Which three actions should you perform in sequence?**

- Create a user-assigned managed identity for the application.
- Create the Azure Functions app with a Premium plan type.
- Create an access policy in Azure Key Vault for the application identity.
- Create an SSL certification in Azure Key Vault for the application identity.
- Create the Azure Functions app with an App Service plan type.
- Create the Azure Functions app with a Consumption plan type.
- Create a system-assigned managed identity for the application.
  
> **1. Create the Azure Functions app with a Premium plan type.**  
> It can be premium or appservice, as it says "add and remove instances of the Azure Functions host" is premium
>
> **2. Create a system-assigned managed identity for the application.**  
> system assigned because it says "Authentication to the Azure Key Vault instance must be removed if the Azure Function application is deleted"
>
> **3. Create an access policy in Azure Key Vault for the application identity.**  
> access policy grants the Azure Functions app permissions to access secrets in the Key Vault.

---

### Q045
**You develop a website. You plan to host the website in Azure. You expect the website to experience high traffic volumes after it is published.   
You must ensure that the website remains available and responsive while minimizing cost.
You need to deploy the website.   
What should you do?**

- Deploy the website to a virtual machine. Configure the virtual machine to automatically scale when the CPU load is high.
- Deploy the website to an App Service that uses the Shared service tier. Configure the App Service plan to automatically scale when the CPU load is high.
- Deploy the website to a virtual machine. Configure a Scale Set to increase the virtual machine instance count when the CPU load is high.
- [Deploy the website to an App Service that uses the Standard service tier. Configure the App Service plan to automatically scale when the CPU load is high.](#q045)

> **Azure App Service** provides a fully managed platform for hosting web applications with built-in support for scaling based on demand. The S**tandard service tier** offers auto-scaling and is suitable for high-traffic applications, providing the necessary resources to keep the website available and responsive.
>
> **Virtual Machines (VMs)** can also be scaled, but they require more maintenance and management, increasing operational complexity and potential costs.
>
> The **Shared tier** is not suitable for high-traffic websites, as it does not support auto-scaling and has limited resources.

- https://chatgpt.com/share/672e6374-af28-8000-a3cf-ae7041b1c0c9

---

### Q046
**A company is developing a Java web app. The web app code is hosted in a GitHub repository located at https://github.com/Contoso/webapp.   
The web app must be evaluated before it is moved to production. You must deploy the initial code release to a deployment slot named staging.   
You need to create the web app and deploy the code.   
How should you complete the commands?**

```
gitrepo=https://github.com/Contoso/webapp
webappname=businesswebapp
resourcegroupname=BusinessAppResourceGroup

az SLOT_1 create --location centralus --name $resourcegroupname

az SLOT_2 create --name $webappname --resource-group $resourcegroupname --sku S3

az SLOT_3 create --name $webappname --resource-group $resourcegroupname --plan $webappname

az SLOT_4 create --name $webappname --resource-group $resourcegroupname --slot staging

az SLOT_5 config --name $webappname --resource-group $resourcegroupname 
--slot staging -repo-url $gitrepo --branch master --manual-integration
```

- SLOT_1
    - [group](#q046)
    - webapp
    - appservice plan
    - webapp deployment slot
    - webapp deployment source
- SLOT_2
    - group
    - webapp
    - [appservice plan](#q046)
    - webapp deployment slot
    - webapp deployment source
- SLOT_3
    - group
    - [webapp](#q046)
    - appservice plan
    - webapp deployment slot
    - webapp deployment source
- SLOT_4
    - group
    - webapp
    - appservice plan
    - [webapp deployment slot](#q046)
    - webapp deployment source
- SLOT_5
    - group
    - webapp
    - appservice plan
    - webapp deployment slot
    - [webapp deployment source](#q046)

> **SLOT_1:** `group create `- Creates a resource group.  
> **SLOT_2:** `appservice plan create` - Creates an App Service plan with the specified SKU.  
> **SLOT_3:** `webapp create` - Creates the web app using the specified plan.  
> **SLOT_4:** `webapp deployment slot create` Creates a deployment slot named `staging`.  
> **SLOT_5:** `webapp deployment source config` - Configures GitHub as the deployment source for the staging slot. 

```bash
# complete command

gitrepo=https://github.com/Contoso/webapp
webappname=businesswebapp
resourcegroupname=BusinessAppResourceGroup

az group create --location centralus --name $resourcegroupname

az appservice plan create --name $webappname --resource-group $resourcegroupname --sku S3

az webapp create --name $webappname --resource-group $resourcegroupname --plan $webappname

az webapp deployment slot create --name $webappname --resource-group $resourcegroupname --slot staging

az webapp deployment source config --name $webappname --resource-group $resourcegroupname   
--slot staging --repo-url $gitrepo --branch master --manual-integration
```

- https://chatgpt.com/share/672f0d09-5b04-8000-9a35-0fc1707859b4
- https://github.com/Azure-Samples/azure-cli-samples/blob/master/app-service/deploy-deployment-slot/deploy-deployment-slot.sh

---

### Q047
**You have a web service that is used to pay for food deliveries. The web service uses Azure Cosmos DB as the data store.   
You plan to add a new feature that allows users to set a tip amount. The new feature requires that a property named tip on the document in Cosmos DB must be present and contain a numeric value.   
There are many existing websites and mobile apps that use the web service that will not be updated to set the tip property for some time.   
How should you complete the trigger?**

```
function ensureTip() {

    var r = SLOT_1
    var i = r.getBody()

    if (SLOT_2) {
        i["tip"] = 0
    }

    SLOT_3
}
```

- SLOT_1
    - __.value()
    - __.readDocument('item')
    - [getContext() .getRequest()](#q047)
    - getContext().getResponse()
- SLOT_2
    - !("tip" in i)
    - request.getValue("tip") === null
    - [isNaN(i["tip"]) || i["tip"] === null](#q047)
    - typeof __.pluck("tip") == 'number'
- SLOT_3
    - [r.setBody(i)](#q047)
    - r.setValue(i)
    - __.upsertDocument(i)
    - __.replaceDocument(i)

> **SLOT_1:** This slot should provide a way to access the incoming request. In Azure Cosmos DB JavaScript triggers, the correct way to access the request object is `getContext().getRequest()`.
>
> **SLOT_2:** This slot needs to check if the `tip` property is either missing or has a non-numeric value. The expression `isNaN(i["tip"]) || i["tip"] === null` will handle both cases by setting `tip` to `0` if tip is either `NaN` or `null`.
>
> **SLOT_3:** After modifying the tip property, we need to update the document body. The correct option here is `r.setBody(i)`, which sets the modified document body back to the request.

```js
// complete trigger
function ensureTip() {

    var r = getContext().getRequest()
    var i = r.getBody()

    if (isNaN(i["tip"]) || i["tip"] === null) {
        i["tip"] = 0
    }

    r.setBody(i)
}
```

- https://chatgpt.com/share/672f10f8-3b00-8000-97b6-009ee940eb83

---

### Q048
**You develop an HTTP triggered Azure Function app to process Azure Storage blob data. The app is triggered using an output binding on the blob.   
The app continues to time out after four minutes. The app must process the blob data.   
You need to ensure the app does not time out and processes the blob data.   
Solution: Use the Durable Function async pattern to process the blob data.   
Does the solution meet the goal?**

- [Yes](#q048)
- No

> Regardless of the function app timeout setting, 230 seconds is the maximum amount of time that an HTTP triggered function can take to respond to a request. This is because of the default idle timeout of Azure Load Balancer. For longer processing times, consider using the Durable Functions async pattern or defer the actual work and return an immediate response.  
> Consider using the "Durable Functions Async Pattern".

- https://chatgpt.com/share/672f1874-9b38-8000-a741-49bf23f92f20
- https://learn.microsoft.com/en-us/azure/azure-functions/functions-scale#timeout

---

### Q049
**You develop an HTTP triggered Azure Function app to process Azure Storage blob data. The app is triggered using an output binding on the blob.   
The app continues to time out after four minutes. The app must process the blob data.
You need to ensure the app does not time out and processes the blob data.   
Solution: Pass the HTTP trigger payload into an Azure Service Bus queue to be processed by a queue trigger function and return an immediate HTTP success response.   
Does the solution meet the goal?**

- [Yes](#q049)
- No
  
> Passing the HTTP trigger payload into an Azure Service Bus queue and having a separate queue-triggered function process the blob data is a valid solution to avoid timeouts. By returning an immediate HTTP success response, the original HTTP-triggered function avoids the timeout issue, while the queue-triggered function handles the longer-running processing in the background. This approach allows for asynchronous processing of the blob data without hitting the four-minute timeout limit.

- https://chatgpt.com/share/672f1874-9b38-8000-a741-49bf23f92f20
- https://learn.microsoft.com/en-us/azure/azure-functions/functions-scale#timeout

---

### Q050
**You develop an HTTP triggered Azure Function app to process Azure Storage blob data. The app is triggered using an output binding on the blob.   
The app continues to time out after four minutes. The app must process the blob data.   
You need to ensure the app does not time out and processes the blob data.   
Solution: Configure the app to use an App Service hosting plan and enable the Always On setting.   
Does the solution meet the goal?**

- Yes
- [No](#q050)

> Regardless of the function app timeout setting, 230 seconds is the maximum amount of time that an HTTP triggered function can take to respond to a request. This is because of the default idle timeout of Azure Load Balancer. For longer processing times, consider using the Durable Functions async pattern or defer the actual work and return an immediate response.  
> The **Always On** setting only ensures the function app remains alive and doesn't go idle, but does not change the timeout for the actual function execution.

- https://chatgpt.com/share/672f1874-9b38-8000-a741-49bf23f92f20
- https://learn.microsoft.com/en-us/azure/azure-functions/functions-scale#timeout

---

### Q051
**You develop a software as a service (SaaS) offering to manage photographs. Users upload photos to a web service which then stores the photos in Azure Storage Blob storage. The storage account type is General-purpose V2.   
When photos are uploaded, they must be processed to produce and save a mobile-friendly version of the image. The process to produce a mobile-friendly version of the image must start in less than one minute.   
You need to design the process that starts the photo processing.   
Solution: Move photo processing to an Azure Function triggered from the blob upload.   
Does the solution meet the goal?**

- [Yes](#q051)
- No

> Using an Azure Function triggered by a blob upload is an effective solution to start processing photos within one minute of upload. Azure Functions can respond to blob storage events quickly, meeting the requirement for near-immediate processing.  
> The latency for an Azure Blob Storage trigger in Azure Functions is typically between 0 to 10 seconds.

- https://chatgpt.com/share/672fc64c-53e0-8000-864e-687df203cc52

---

### Q052
**You plan to create a Docker image that runs an ASP.NET Core application named ContosoApp. You have a setup script named `setupScript.ps1` and a series of application files including `ContosoApp.dll`.   
You need to create a Dockerfile document that meets the following requirements:   
• Call `setupScripts.ps1` when the container is built.   
• Run `ContosoApp.dll` when the container starts.   
The Dockerfile document must be created in the same folder where `ContosoApp.dll` and `setupScript.ps1` are stored.   
Which five commands should you use to develop the solution? To answer, move the appropriate commands from the list of commands to the answer area and arrange them in the correct order.**

- FROM microsoft/aspnetcore:latest
- WORKDIR /apps/ContosoApp
- CMD ["dotnet", "ContosoApp.dll"]
- COPY ./ .
- RUN powershell ./setupScript.ps1

> 1. **Specify the base image** - This should be a version of ASP.NET Core.  
> `FROM mcr.microsoft.com/dotnet/aspnet:latest`
>
> 2. **Set the working directory** - This is the directory where the application files are stored.  
> `WORKDIR /apps/ContosoApp`
>
> 3. **Copy files into the container** - Copy all necessary files from the host to the container.  
> `COPY ./ .`
>
> 4. **Run the setup script** - Run the setup script when the container is built.  
> `RUN powershell ./setupScript.ps1`
>
> 5. **Specify the command to start the application** - Define how to run `ContosoApp.dll` when the container starts.  
> `CMD ["dotnet", "ContosoApp.dll"]`

```dockerfile
FROM mcr.microsoft.com/dotnet/aspnet:latest
WORKDIR /apps/ContosoApp
COPY ./ .
RUN powershell ./setupScript.ps1
CMD ["dotnet", "ContosoApp.dll"]
```

- https://chatgpt.com/share/672fcb9d-3904-8000-b357-e48a00f41ca7

---

### Q053
**You are developing an Azure Function App that processes images that are uploaded to an Azure Blob container.   
Images must be processed as quickly as possible after they are uploaded, and the solution must minimize latency.  
You create code to process images when the Function App is triggered.   
You need to configure the Function App.   
What should you do?**

- Use an App Service plan. Configure the Function App to use an Azure Blob Storage input trigger.
- Use a Consumption plan. Configure the Function App to use an Azure Blob Storage trigger.
- Use a Consumption plan. Configure the Function App to use a Timer trigger.
- [Use an App Service plan. Configure the Function App to use an Azure Blob Storage trigger.](#q053)
- Use a Consumption plan. Configure the Function App to use an Azure Blob Storage input trigger.
  
> **Consumption plan** can cause a 10-min delay in processing new blobs if a function app has gone idle. To avoid this latency, you can switch to an App Service plan with Always On enabled.  
> there is no such thing as **input trigger** it is **input binding**.

- https://docs.microsoft.com/en-us/azure/azure-functions/functions-bindings-storage-blob-trigger?tabs=csharp

---

### Q054
**You are configuring a new development environment for a Java application.  
The environment requires a Virtual Machine Scale Set (VMSS), several storage accounts, and networking components.  
The VMSS must not be created until the storage accounts have been successfully created and an associated load balancer and virtual network is configured.  
How should you complete the Azure Resource Manager template?**

```
{
    ...
    "resources": [
        {
            "apiVersion": "2016-01-01",
            "type": "Microsoft. Storage/storageAccounts",
            "name": "[concat(SLOT_1(), 'storage', uniqueString(resourceGroup().id))]",
            "location": "[resourceGroup().location]",
            ...
            "sku": {
                "name": "Standard_LRS"
            },
            "kind": "Storage",
            "properties": {},
            "SLOT_2": {
                "name": "storagesetup",
                "count": 3
            }
        },
        {
            "apiVersion": "2015-06-15",
            "type": "Microsoft.Compute/virtualMachines",
            "name": "[concat('vm', uniqueString(resourceGroup().id))]",
            "SLOT_3": [
                "[variables('loadBalancerName')]",
                "[variables('virtualNetworkName')]",
                "storagesetup"
            ],
            ...
        }
    ],
    "outputs": {}
}

```

- SLOT_1
    - copy
    - [copyIndex](#q054)
    - priotity
    - dependsOn
- SLOT_2
    - [copy](#q054)
    - copyIndex
    - priotity
    - dependsOn
- SLOT_3
    - copy
    - copyIndex
    - priotity
    - [dependsOn](#q054)

> **SLOT_1:** copyIndex is used in the name field to provide a unique identifier for each storage account created in the loop.   
> **SLOT_2:** copy specifies the settings for the loop, creating 3 storage accounts.  
> **SLOT_3:** dependsOn ensures that the Virtual Machine Scale Set (VMSS) only starts deployment after the storage accounts, load balancer, and virtual network have been created.  

- https://chatgpt.com/share/67304c59-6808-8000-bcbe-7486594f77e6
- https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/copy-resources
- https://learn.microsoft.com/en-us/azure/virtual-machine-scale-sets/quick-create-template-windows
- https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/resource-dependency

---

### Q055
**You are developing an Azure Function App by using Visual Studio.  
The app will process orders input by an Azure Web App.  
The web app places the order information into Azure Queue Storage.  
You need to review the Azure Function App code shown below.**

```csharp
public static class OrderProcessor 
{
    [FunctionName("ProcessOrders") ]
    public static void ProcessOrders([QueueTrigger ("incoming-orders") ]CloudQueueMessage myQueueltem, [Table("Orders")]ICollector<Order> tableBindings, TraceWriter log)
    {
        log.Info($"Processing Order: {myQueueItem.Id}");
        log.Info($"Queue Insertion Time: {myQueueItem. InsertionTime}");
        log.Info($"Queue Expiration Time: {myQueueItem.ExpirationTime}");
        tableBindings.Add(JsonConvert.Deserialize0bject«Order>(myQueueItem.AsString));
    }

    [FunctionName("ProcessOrders-Poison")]
    public static void ProcessFailedOrders([QueueTrigger ("incoming-orders-poison") ]CloudQueueMessage myQueueItem, TraceWriter log)
    {
        log.Error($"Failed to process order: {myQueueItem.AsString})");
        ...
    }
}
```

- The code will log the time that the order was processed from the queue.
    - Yes
    - [No](#q055)
> **No**, It logs the following:  
> - **ExpirationTime** - The time that the message expires.  
> - **InsertionTime** - The time that the message was added to the queue.  

- When the `ProcessOrders` function fails, the function will retry up to five times for a given order, including the first try.
    - [Yes](#q055)
    - No
> **Yes**, `maxDequeueCount`: The number of times to try processing a message before moving it to the poison queue. Default value is **5**.

- When there are multiple orders in the queue, a batch of orders will be retrieved from the queue and the `ProcessOrders` function will run multiple instances concurrently to process the orders.
    - [Yes](#q055)
    - No
> **Yes**, When there are multiple queue messages waiting, the queue trigger retrieves a batch of messages and invokes function instances concurrently to process them. By default, the batch size is 16. When the number being processed gets down to 8, the runtime gets another batch and starts processing those messages. So the maximum number of concurrent messages being processed per function on one virtual machine (VM) is 24.

- The `ProcessOrders` function will output the order to an Orders table in Azure Table Storage.
    - [Yes](#q055)
    - No
> **Yes**, The function uses the `tableBindings` parameter, an `ICollector<Order>` bound to the "Orders" table, to add orders to Azure Table Storage.

---

### Q056
**You are developing a solution for a hospital to support the following use cases:  
• The most recent patient status details must be retrieved even if multiple users in different locations have updated the patient record.  
• Patient health monitoring data retrieved must be the current version or the prior version.  
• After a patient is discharged and all charges have been assessed, the patient billing record contains the final charges.  
You provision a Cosmos DB NoSQL database and set the default consistency level for the database account to Strong. You set the value for Indexing Mode to
Consistent.  
You need to minimize latency and any impact to the availability of the solution. You must override the default consistency level at the query level to meet the required consistency guarantees for the scenarios.  
Which consistency levels should you implement?**

- Return the most recent patient status.
    - [Strong](#q056)
    - Bounded Staleness
    - Consistent Prefix
    - Eventual
- Return health monitoring data that is no less than one version behind.
    - [Strong](#q056)
    - Bounded Staleness
    - Consistent Prefix
    - Eventual
- After patient is discharged and all charges are assessed, retrieve the correct billing data with the final charges.
    - Strong
    - Bounded Staleness
    - Consistent Prefix
    - [Eventual](#q056)

> Return the most recent patient status : **Strong**  
> Strong consistency offers a linearizability guarantee. The reads are guaranteed to return the most recent committed version of an item. A client never sees an uncommitted or partial write. Users are always guaranteed to read the latest committed write.
>
> Return health monitoring data that is no less than one version behind : **Strong**
> Bounded staleness The reads are guaranteed to honor the consistent-prefix guarantee. The reads might lag behind writes by at most "K" versions of an item or by "t" time interval.  
> However, For a single region account, the minimum value of K and T is 10 write operations or 5 seconds. For multi-region accounts the minimum value of K and T is 100,000 write operations or 300 seconds.
> Therefore, in order to ensure data is no less than once version behind, Strong consistency should be used.

> After patient is discharged and all charges are assessed, retrieve the correct billing data with the final charges : **Eventual**  
> In the absence of any further writes, the replicas eventually converge.

- https://chatgpt.com/share/6730b940-a248-8000-96ef-4583c120e01f
- https://learn.microsoft.com/en-us/azure/cosmos-db/consistency-levels

---

### Q057
**You are configuring a development environment for your team. You deploy the latest Visual Studio image from the Azure Marketplace to your Azure subscription.  
The development environment requires several software development kits (SDKs) and third-party components to support application development across the organization.  
You install and customize the deployed virtual machine (VM) for your development team. The customized VM must be saved to allow provisioning of a new team member development environment.  
You need to save the customized VM for future provisioning.
Which tools or services should you use?**

- To Generalize the VM
    - [Azure PowerShell](#q057)
    - Visual Studio command prompt
    - Azure Migrate
    - Azure Backup

- To Store the images
    - [Azure Blob Storage](#q057)
    - Azure Data Lake Storage
    - Azure File Storage
    - Azure Table Storage

> **Azure PowerShell**
> Creating an image directly from the VM ensures that the image includes all of the disks associated with the VM, including the OS disk and any data disks. Before you begin, make sure that you have the latest version of the Azure PowerShell module. You use Sysprep to generalize the virtual machine, then use Azure PowerShell to create the image.  
>
> **Azure Blob Storage**
> A VM Image is a collection of metadata and pointers to a set of VHDs (one VHD per disk) stored as page blobs in Azure Storage.


- https://azure.microsoft.com/en-us/blog/vm-image-blog-post/
- https://learn.microsoft.com/en-us/azure/virtual-machines/capture-image-resource

---

### Q058
**You are preparing to deploy a website to an Azure Web App from a GitHub repository. The website includes static content generated by a script.  
You plan to use the Azure Web App continuous deployment feature.  
You need to run the static generation script before the website starts serving traffic.  
What are two possible ways to achieve this goal?**

- Add the path to the static content generation tool to WEBSITE_RUN_FROM_PACKAGE setting in the host.json file.
- [Add a PreBuild target in the websites csproj project file that runs the static content generation script.](#q058)
- Create a file named run.cmd in the folder /run that calls a script which generates the static content and deploys the website.
- [Create a file named .deployment in the root of the repository that calls a script which generates the static content and deploys the website.](#q058)

> **Add a PreBuild target in the website's `.csproj` project file that runs the static content generation script.**  
> The `PreBuild` target allows you to specify tasks that should run before the build process begins. By adding the static content generation script here, it will execute before the deployment completes, ensuring the static content is generated.  
>
> **Create a file named `.deployment` in the root of the repository that calls a script which generates the static content and deploys the website.**
> The `.deployment` file in Azure App Service provides a way to specify custom deployment actions. You can configure it to run the static generation script before the website goes live.
>
> Adding the path to `WEBSITE_RUN_FROM_PACKAGE` is unrelated to running scripts and is used to indicate that the app runs directly from a package file.
> 
>  Creating a `run.cmd` in the `/run` folder is not a recognized Azure deployment approach and would not ensure the script runs as required.

- https://chatgpt.com/share/6730bf88-a4fc-8000-b79f-d286db993944

---

### Q059
**You are developing an application to use Azure Blob storage. You have configured Azure Blob storage to include change feeds.  
A copy of your storage account must be created in another region. Data must be copied from the current storage account to the new storage account directly between the storage servers.  
You need to create a copy of the storage account in another region and copy the data.  
In which order should you perform the actions?**

- Use AZCopy to copy the data to the new storage account.
- Deploy the template to create a new storage account in the target region.
- Export a Resource Manager template.
- Create a new template deployment.
- Modify the template by changing the storage account name and region.

> 1. **Export a Resource Manager template** - Export the template to capture the configuration of the existing storage account.  
> 2. **Create a new template deployment** -Initiate a new deployment using the exported template, which will be modified next.  
> 3. **Modify the template by changing the storage account name and region** - Update the template to reflect the new storage account name and target region.
> 4. **Deploy the template to create a new storage account in the target region** - Deploy the modified template to create the new storage account in the chosen region.
> 5. **Use AZCopy to copy the data to the new storage account** - Finally, use AZCopy to perform a direct copy of data between the source and destination storage accounts.

- https://learn.microsoft.com/en-us/azure/operational-excellence/relocation-storage-account?tabs=azure-portal
---

### Q060
**You are preparing to deploy an Azure virtual machine (VM)-based application.  
The VMs that run the application have the following requirements:  
• When a VM is provisioned the firewall must be automatically configured before it can access Azure resources.  
• Supporting services must be installed by using an Azure PowerShell script that is stored in Azure Storage.  
You need to ensure that the requirements are met.  
Which features should you use?**

**Requirements:**
- Firewall Configuration
    - [Run Command](#q060)
    - Serial console
    - Hybrid Runbook Worker
    - Custom Script Extension

- Supporting services script
    - Run Command
    - Serial console
    - Hybrid Runbook Worker
    - [Custom Script Extension](#q060)


> **Run Command**: This capability is useful in all scenarios where you want to run a script within a VM. It's one of the only ways to troubleshoot and remediate a VM that doesn't have the RDP or SSH port open, because of improper network or administrative user configuration.
>
> **Customer Script Extension**: The Custom Script Extension downloads and executes scripts on Azure virtual machines. This extension is useful for post deployment configuration, software installation, or any other configuration or management tasks. Scripts can be downloaded from Azure storage or GitHub, or provided to the Azure portal at extension run time. The Custom Script Extension integrates with Azure Resource Manager templates, and can be run using the Azure CLI, PowerShell, Azure portal, or the Azure Virtual Machine REST API.

- https://chatgpt.com/share/6730c79d-4814-8000-9ff8-a36c843b6bf9
- https://learn.microsoft.com/en-us/azure/virtual-machines/windows/run-scripts-in-vm

---

### Q061
**A company is developing a Node.js web app. The web app code is hosted in a GitHub repository located at https://github.com/TailSpinToys/webapp.  
The web app must be reviewed before it is moved to production. You must deploy the initial code release to a deployment slot named review.  
You need to create the web app and deploy the code.  
How should you complete the commands?**

```
$gitrepo="https://github.com/TailSpinToys/webapp"
$webappname="TailSpinToysWeb"
$location="WestUS2"

SLOT_1 -Name myResourceGroup -Location $location

SLOT_2-Name $webappname -Location $location -ResourceGroupName myResourceGroup -Tier Standard

SLOT_3 -Name $webappname -Location $location -AppServicePlan $webappname -ResourceGroupName myResourceGroup

SLOT_4 -Name $webappname -ResourceGroupName myResourceGroup -Slot review

$PropertiesObject = @{repoUrl="$gitrepo"; branch="master";}

Set-AzResource -PropertyObject $PropertiesObject -ResourceGroupName myResourceGroup -ResourceType Microsoft. Web/sites/slots/sourcecontrols 
-ResourceName $webappname/review/web 
-ApiVersion 2015-08-01 -Force

Switch-AzWebAppSlot -Name $webappname -ResourceGroupName myResourceGroup
-SourceSlotName review -DestinationSlotName production
```

- SLOT_1
    - New-AzWebAppSlot
    - New-AzWebApp
    - New-AzAppServicePlan
    - [New-AzResourceGroup](#q061)
- SLOT_2
    - New-AzWebAppSlot
    - New-AzWebApp
    - [New-AzAppServicePlan](#q061)
    - New-AzResourceGroup
- SLOT_3
    - New-AzWebAppSlot
    - [New-AzWebApp](#q061)
    - New-AzAppServicePlan
    - New-AzResourceGroup
- SLOT_4
    - [New-AzWebAppSlot](#q061)
    - New-AzWebApp
    - New-AzAppServicePlan
    - New-AzResourceGroup

> **SLOT_1** - You need to create a **resource group** for your web app and other resources. Therefore, the correct cmdlet is `New-AzResourceGroup`.  
> **SLOT_2** - You need to create an **App Service Plan** for your web app. The correct cmdlet is `New-AzAppServicePlan`.  
> **SLOT_3** - You need to create a **web app** for your project. The correct cmdlet is `New-AzWebApp`.  
> **SLOT_4** - You need to create a **deployment slot** named "review" for your web app. The correct cmdlet is `New-AzWebAppSlot`.

```powershell
# complete powershell command

$gitrepo="https://github.com/TailSpinToys/webapp"
$webappname="TailSpinToysWeb"
$location="WestUS2"

New-AzResourceGroup -Name myResourceGroup -Location $location

New-AzAppServicePlan -Name $webappname -Location $location -ResourceGroupName myResourceGroup -Tier Standard

New-AzWebApp -Name $webappname -Location $location -AppServicePlan $webappname -ResourceGroupName myResourceGroup

New-AzWebAppSlot -Name $webappname -ResourceGroupName myResourceGroup -Slot review

$PropertiesObject = @{repoUrl="$gitrepo"; branch="master";}

Set-AzResource -PropertyObject $PropertiesObject -ResourceGroupName myResourceGroup -ResourceType Microsoft.Web/sites/slots/sourcecontrols -ResourceName $webappname/review/web -ApiVersion 2015-08-01 -Force

Switch-AzWebAppSlot -Name $webappname -ResourceGroupName myResourceGroup -SourceSlotName review -DestinationSlotName production
```

- https://chatgpt.com/share/6730eb27-c2a4-8000-bca0-0f63f66b7153

---

### Q062
**You are developing an application that needs access to an Azure virtual machine (VM).  
The access lifecycle for the application must be associated with the VM service instance.  
You need to enable managed identity for the VM.  
How should you complete the PowerShell segment?**

```
$vm = Get-AzVM -ResourceGroupName "ContosoRG" -Name "ContosoVM"
Update-AzVM -ResourceGroupName "ContosoRG" - VM $vm -SLOT_1 SLOT_2
```

- SLOT_1
    - AssignIdentity
    - [IdentityType](#q062)
- SLOT_2
    - [$SystemAssigned](#q062)
    - $UserAssigned

> **SLOT_1 (IdentityType)**: This specifies the type of managed identity to be used. The correct value here is `SystemAssigned`, which means the VM will have a system-assigned managed identity.  
> **SLOT_2 ($SystemAssigned)**: This indicates that the VM will have a system-assigned identity, meaning Azure will automatically create and manage the identity for the VM.

```powershell
# complete powershell command

$vm = Get-AzVM -ResourceGroupName "ContosoRG" -Name "ContosoVM"
Update-AzVM -ResourceGroupName "ContosoRG" -VM $vm -IdentityType SystemAssigned
```

- https://chatgpt.com/share/6730ec00-6474-8000-b0db-0619c3d489e8

---

### Q063
**You develop a software as a service (SaaS) offering to manage photographs.   
Users upload photos to a web service which then stores the photos in Azure Storage Blob storage. The storage account type is General-purpose V2.  
When photos are uploaded, they must be processed to produce and save a mobile-friendly version of the image. The process to produce a mobile-friendly version of the image must start in less than one minute.  
You need to design the process that starts the photo processing.  
Solution: Create an Azure Function app that uses the Consumption hosting model and that is triggered from the blob upload.  
Does the solution meet the goal?**

- Yes
- [No](#q063)

> The Consumption plan is not ideal for scenarios where a process needs to start in less than one minute consistently, as it might experience delays due to the cold start behavior.  
> To meet the goal of processing the photos in less than one minute, a better solution would be to use the Premium or Dedicated (App Service) plan for the Azure Function app. 

- https://chatgpt.com/share/6730ed6c-6e00-8000-9158-c6a4da5a9fed

---

### Q064
**You develop and deploy an Azure App Service API app to a Windows-hosted deployment slot named Development.  
You create additional deployment slots named Testing and Production. You enable auto swap on the Production deployment slot.  
You need to ensure that scripts run and resources are available before a swap operation occurs.  
Solution: Update the app with a method named `statuscheck` to run the scripts. Update the app settings for the app. Set the `WEBSITE_SWAP_WARMUP_PING_PATH` and `WEBSITE_SWAP_WARMUP_PING_STATUSES` with a path to the new method and appropriate response codes.   
Does the solution meet the goal?**

- [Yes](#q064)
- No
  
> In Azure App Service, when performing a swap between deployment slots, you can configure the app to wait for resources to be ready before completing the swap. The `WEBSITE_SWAP_WARMUP_PING_PATH` setting specifies a URL path that the swap process will call to ensure the application is ready. The `WEBSITE_SWAP_WARMUP_PING_STATUSES` setting specifies which HTTP status codes are considered successful for the warm-up check (e.g., 200 OK).  
> 
> **WEBSITE_SWAP_WARMUP_PING_PATH:** The path to ping to warm up your site. Add this app setting by specifying a custom path that begins with a slash as the value. An example is `/statuscheck.` The default value is `/`.  
> **WEBSITE_SWAP_WARMUP_PING_STATUSES:** Valid HTTP response codes for the warm-up operation. Add this app setting with a comma-separated list of HTTP codes. An example is 200,202 . If the returned status code isn't in the list, the warmup and swap operations are stopped. By default, all response codes are valid.  
> **WEBSITE_WARMUP_PATH:** A relative path on the site that should be pinged whenever the site restarts (not only during slot swaps). Example values include `/statuscheck` or the root path, `/`.

- https://chatgpt.com/share/6730efa6-894c-8000-829e-24f417422ac5
- https://learn.microsoft.com/en-us/azure/app-service/deploy-staging-slots?tabs=portal#specify-custom-warm-up

---

### Q065
**You create the following PowerShell script:**
```powershell
$source = New-AzScheduledQueryRuleSource -Query 'Heartbeat | where TimeGenerated > ago(1h)' -DataSourceId "contoso"

$schedule = New-AzScheduledQueryRuleSchedule -FrequencyInMinutes 60 -TimeWindowInMinutes 60

$triggerCondition = New-AzScheduledQueryRuleTriggerCondition -ThresholdOperator "LessThan" -Threshold 5

$aznsActionGroup = New-AzScheduledQueryRuleAznsActionGroup -ActionGroup "contoso" 
-EmailSubject "Custom email subject" 
-CustomWebhookPayload "{ "'alert'": "'#alertrulename'", "'IncludeSearchResults'": true }"

$alertingAction = New-AzScheduledQueryRuleAlertingAction -AznsAction SaznsActionGroup 
-Severity "3" -Trigger $triggerCondition

New-AzScheduledQueryRule -ResourceGroupName "contoso" -Location "eastus" 
-Action $alertingAction -Enabled $true 
-Description "Alert description" -Schedule $schedule 
-Source $source -Name "Alert Name"
```
-**For each of the following statements, select Yes if the statement is true. Otherwise, select No.**

- **A log alert is created that sends an email when the CPU percentage is above 60 percent for five minutes.**
  - Yes
  - [No](#q065)

> The script does not mention CPU percentage at all. It instead uses the `Heartbeat` table and checks if the number of heartbeats in the past hour is less than five. Additionally, the `triggerCondition` threshold is set to 5, not 60%.

- **A log alert is created that sends an email when the number of virtual machine heartbeats in the past hour is less than five.**
  - [Yes](#q065)
  - No
  
> The query in the script looks for `Heartbeat` entries where `TimeGenerated` is within the last hour (`ago(1h)`), and the threshold is set to 5. This matches the number of heartbeats being less than 5.

- **The log alert is scheduled to run every two hours.**
  - Yes
  - [No](#q065)

> The script specifies the schedule as `-FrequencyInMinutes 60`, meaning the alert will run every 60 minutes (1 hour), not two hours.

> **Summary:**
> - The script creates an Azure Scheduled Query Rule that runs a query every hour, checking the number of heartbeats in the last hour.    
> - If the number of heartbeats is less than 5, the rule triggers an alert with an action group that sends an email and performs a webhook action.  
> - The alert is created in the "contoso" resource group, in the "eastus" region.

- https://chatgpt.com/share/6730f4d2-d118-8000-9eb3-d148484f723a

---

### Q066
**You are developing an Azure Function app.  
The app must meet the following requirements:  
• Enable developers to write the functions by using the Rust language.  
• Declaratively connect to an Azure Blob Storage account.  
You need to implement the app.  
Which Azure Function app features should you use?**  

**Requirements:**

- **Enable developers to write the functions by using the Rust language.**
    - [Custom handler](#q066)
    - Extension bundle
    - Trigger
    - Runtime
    - Policy
    - Hosting plan

> Azure Functions natively support languages like C#, JavaScript, Python, etc., but Rust is not natively supported. To use Rust, a **custom handler** is needed, as it allows developers to bring functions written in any language by defining a custom executable that Azure Functions can use.

- **Declaratively connect to an Azure Blob Storage account.**
    - Custom handler
    - [Extension bundle](#q066)
    - Trigger
    - Runtime
    - Policy
    - Hosting plan

> With custom handlers, you can use triggers and input and output bindings via **extension bundles**.  

```json
// host.json

{
  "version": "2.0",
  "customHandler": {
    "description": {
      "defaultExecutablePath": "handler.exe"
    }
  },
  "extensionBundle": {
    "id": "Microsoft.Azure.Functions.ExtensionBundle",
    "version": "[1.*, 2.0.0)"
  }
}
```

- https://chatgpt.com/share/6730f8ce-1a30-8000-bb4d-d0f5a18258a4
- https://learn.microsoft.com/en-us/azure/azure-functions/functions-custom-handlers

---

### Q067
**You are developing an ASP.NET Core web application. You plan to deploy the application to Azure Web App for Containers.  
The application needs to store runtime diagnostic data that must be persisted across application restarts. You have the following code:**
```csharp
public void SaveDiagData (string data) {
    var path = Environment.GetEnvironmentVariable("DIAGDATA");
    File.WriteAllText(Path.Combine(path, "data"), data);
}
```
**You need to configure the application settings so that diagnostic data is stored as required.  
How should you configure the web app's settings?**
```
SLOT_1=true
DIAGDATA=SLOT_2
```

- SLOT_1
    - LOCALAPPDATA
    - WEBSITE_LOCALCACHE_ENABLED
    - DOTNET_HOSTING_OPTIMIZATION_CACHE
    - [WEBSITES_ENABLE_APP_SERVICE_STORAGE](#q067)
- SLOT_2
    - [/home](#q067)
    - /local
    - D:\home
    - D:\local

> **WEBSITES_ENABLE_APP_SERVICE_STORAGE:**   
> Setting `WEBSITES_ENABLE_APP_SERVICE_STORAGE` to `true` enables persistent storage in Azure Web App for Containers. This setting allows data stored in specific directories (like `/home`) to persist even if the container restarts.
>
> **DIAGDATA Path:**
> `/home` is a persistent directory in the Azure App Service environment. Using `/home` as the `DIAGDATA` path ensures that diagnostic data written to this location will be retained across container restarts.  
> For Windows,it would be `C:\home`, which is not a provided option. but `/home` is provided.

- https://chatgpt.com/share/6730fc52-4ce4-8000-83f8-f9b8a3db6df7
- https://learn.microsoft.com/en-us/azure/app-service/configure-custom-container?pivots=container-linux&tabs=debian
- https://learn.microsoft.com/en-us/azure/app-service/configure-custom-container?pivots=container-windows&tabs=debian

---

### Q068
**You are developing a web app that is protected by Azure Web Application Firewall (WAF). 
All traffic to the web app is routed through an Azure Application Gateway instance that is used by multiple web apps. The web app address is contoso.azurewebsites.net.  
All traffic must be secured with SSL. The Azure Application Gateway instance is used by multiple web apps.  
You need to configure the Azure Application Gateway for the web app.  
Which two actions should you perform?**

- [In the Azure Application Gateway's HTTP setting, enable the Use for App service setting.](#q068)
- Convert the web app to run in an Azure App service environment (ASE).
- [Add an authentication certificate for contoso.azurewebsites.net to the Azure Application Gateway.](#q068)
- In the Azure Application Gateway's HTTP setting, set the value of the Override backend path option to contoso22.azurewebsites.net.


> **In the Azure Application Gateway's HTTP setting, enable the Use for App service setting.**  
> Enabling this setting allows the Application Gateway to communicate directly with the Azure App Service (in this case, contoso.azurewebsites.net) over its secure endpoint without requiring an additional certificate configuration on the Application Gateway. This simplifies SSL configuration for App Services, as the Application Gateway can handle the SSL connections securely to the App Service.
>
> **Add an authentication certificate for contoso.azurewebsites.net to the Azure Application Gateway.**  
> Adding an authentication certificate is necessary to validate the backend service's SSL certificate (the SSL certificate for contoso.azurewebsites.net). This ensures the connection between the Application Gateway and the web app is secure and trusted.
>
> **~~Convert the web app to run in an Azure App Service Environment (ASE).~~**   
> Running the app in an ASE is not required to use Azure Application Gateway or WAF. ASEs are primarily used for isolated, dedicated environments and are not relevant to this specific requirement of securing traffic through Application Gateway.
>
> **~~Set the Override backend path option to contoso22.azurewebsites.net.~~**  
> Changing the backend path is unnecessary here, as it would redirect traffic to a different hostname (contoso22.azurewebsites.net), which is incorrect and could cause routing issues.

- https://chatgpt.com/share/6730ff59-3a68-8000-ace5-e9b92472c0f0

---

### Q069
**You are developing a web application that runs as an Azure Web App. The web application stores data in Azure SQL Database and stores files in an Azure  
Storage account. The web application makes HTTP requests to external services as part of normal operations.  
The web application is instrumented with Application Insights. The external services are OpenTelemetry compliant.  
You need to ensure that the customer ID of the signed in user is associated with all operations throughout the overall system.  
What should you do?**

- [Add the customer ID for the signed in user to the CorrelationContext in the web application](#q069)
- On the current SpanContext, set the TraceId to the customer ID for the signed in user
- Set the header Ocp-Apim-Trace to the customer ID for the signed in user
- Create a new SpanContext with the TraceFlags value set to the customer ID for the signed in user

> The best approach to ensure the customer ID of the signed-in user is associated with all operations is to **add the customer ID to the CorrelationContext** in the web application. This method is recommended because `CorrelationContext` allows you to add custom properties (such as a customer ID) that will propagate with the telemetry data across distributed services.
>
> Here's why other options are not relevant:  
> **On the current SpanContext, set the TraceId to the customer ID for the signed in user:** This is not appropriate because `TraceId` is meant for identifying traces, not for storing user identifiers.  
> **Set the header Ocp-Apim-Trace to the customer ID for the signed in user:** This option is incorrect because `Ocp-Apim-Trace` is typically used in Azure API Management for tracing requests, not for associating customer-specific data.  
> **Create a new SpanContext with the TraceFlags value set to the customer ID for the signed in user:** This is incorrect, as `TraceFlags` is used for sampling and trace status, not for holding custom identifiers like customer IDs.

- https://chatgpt.com/share/67310176-c5f0-8000-b8dc-ff9518f384e9

---

### Q070
**You are developing an Azure Function App. You develop code by using a language that is not supported by the Azure Function App host. The code language supports HTTP primitives.  
You must deploy the code to a production Azure Function App environment.  
You need to configure the app for deployment.  
Which configuration values should you use?**

**Configuration Patameters:**
- **Publish**
    - Code
    - [Docker Container](#q070)

- **Runtime Stack**
    - Node.js
    - Python
    - PowerShell Core
    - [Custom Handler](#q070)

- **Version**
    - 14 LTS
    - 7.0
    - [custom](#q070)

> **Publish:** Docker Container  
> A custom handler can be deployed to every Azure Functions hosting option. If your handler requires operating system or platform dependencies (such as a language runtime), you may need to use a custom container. You can create and deploy your code to Azure Functions as a custom Docker container.  
> This will allow you to package your application with the necessary dependencies and runtime using a custom container image.   
>
> **Runtime Stack:** Custom Handler  
> This option is for functions that are triggered by custom handlers, enabling the use of any language that can process HTTP requests.  
>
> **Version:** custom  
> Since you're not using a predefined runtime, select custom as the version

- https://chatgpt.com/share/67310498-2f44-8000-91fa-cd0d819f46d1

---

### Q071
**You develop a software as a service (SaaS) offering to manage photographs. Users upload photos to a web service which then stores the photos in Azure Storage Blob storage. The storage account type is General-purpose V2.  
When photos are uploaded, they must be processed to produce and save a mobile-friendly version of the image. The process to produce a mobile-friendly version of the image must start in less than one minute.  
You need to design the process that starts the photo processing.  
Solution: Use the Azure Blob Storage change feed to trigger photo processing.  
Does the solution meet the goal?**

- Yes
- [No](#q071)

> The Azure Blob Storage change feed is designed for tracking and auditing changes over time, but it is not suitable for triggering real-time or near real-time processing due to its latency. Change feed captures blob creation, modification, and deletion events, but it is not meant for immediate triggering of processes as it can take several minutes or longer to update.

- https://chatgpt.com/share/67317f18-2b50-8000-a8c8-75cf701e7f82
- https://learn.microsoft.com/en-us/azure/storage/blobs/storage-blob-change-feed?tabs=azure-portal

---

### ~~Q072~~
**You provision virtual machines (VMs) as development environments.  
One VM does not start. The VM is stuck in a Windows update process. You attach the OS disk for the affected VM to a recovery VM.  
You need to correct the issue.  
In which order should you perform the actions?**

- Run the following command at an elevated command prompt:  
    `dism /image: \ /get=packages > c:\temp \Patch. txt`
- Run the following command at an elevated command prompt:  
    `dism / Image:<Attached OS disks>:\ / RemovePackage /PackageName:<package name to delete>`
- Detach the OS disk and recreate the VIM
- Open C: \temp\Patch.txt file and locate the update that is in a pending state


> 1. **Run the following command at an elevated command prompt:**  
> `dism /image:<Attached OS disk>:\ /get-packages > c:\temp\Patch.txt`  
> This command lists all installed packages on the attached OS disk and outputs them to a file, helping identify the problematic update.
>
> 2. **Open C:\temp\Patch.txt file and locate the update that is in a pending state.**  
> Open the file to identify the update package that is causing the VM to hang.
>
> 3. **Run the following command at an elevated command prompt:**  
> `dism /image:<Attached OS disk>:\ /remove-package /PackageName:<package name to delete>`  
> Use this command to remove the problematic update package identified in the previous step.
>
> 4. **Detach the OS disk and recreate the VM.**  
> After removing the problematic update, detach the OS disk from the recovery VM, reattach it to the original VM, and then restart it to verify that it boots correctly.

- https://chatgpt.com/share/67318210-b40c-8000-b156-ace9585c8a97
- https://learn.microsoft.com/en-us/troubleshoot/azure/virtual-machines/windows/troubleshoot-stuck-updating-boot-error

---

### Q073
**You develop an HTTP triggered Azure Function app to process Azure Storage blob data. The app is triggered using an output binding on the blob.  
The app continues to time out after four minutes. The app must process the blob data. You need to ensure the app does not time out and processes the blob data.  
Solution: Update the functionTimeout property of the host.json project file to 10 minutes.  
Does the solution meet the goal?**

- Yes
- [No](#q073)

> Regardless of the function app timeout setting, 230 seconds is the maximum amount of time that an HTTP triggered function can take to respond to a request. 

- https://learn.microsoft.com/en-us/azure/azure-functions/functions-scale#timeout

---

### Q074
You are developing an Azure Durable Function based application that processes a list of input values. The application is monitored using a console application that retrieves JSON data from an Azure Function diagnostic endpoint.  
During processing a single instance of invalid input does not cause the function to fail. Invalid input must be available to the monitoring application.  
You need to implement the Azure Durable Function and the monitoring console application.
How should you complete the code segments?   

```
[FunctionName("App" )]|
public static async Task<List<string>> RunOrchestrator ([OrchestrationTrigger] IDurableOrchestrationContext context) 
{
    Entityid[] input = ...
    int errindex = ...
    SLOT_1;

}

using (var client = new HttpClient())
{
    while (true){
        var response = await client.GetAsync("...");
        response.EnsureSuccessStatusCode();
        var json = await response.Content.ReadAsStringÄsync();
        dynamic result = JsonConvert.DeserializeObject(json);
        if (result.runtimeStatus == "SLOT_2"){
            return result.SLOT_3;
        }
    }
}   
```

- SLOT_1
    - context.SetOutput(input[errindex])
    - context.SetCustomStatus(input[errindex])
    - context.SignalEntity(input[errindex], "error")
    - await context.CallEntityAsync(input[errindex], "error")

- SLOT_2
    - Failed
    - Awaited
    - Listening
    - Completed

- SLOT_3
    - input
    - output
    - runtimeStatus
    - customStatus

---

### Q075
**You are developing an Azure Durable Function to manage an online ordering process.  
The process must call an external API to gather product discount information.  
You need to implement the Azure Durable Function.  
Which Azure Durable Function types should you use?**

- [Orchestrator](#q075)
- Entity
- Client
- [Activity](#q075)

> **Orchestrator** - This function type coordinates the workflow, managing the sequence of function calls, including any decision-making processes, such as calling an external API to get discount information and managing order-related tasks.  
>
> **Activity** - This function type performs tasks such as calling external services or performing CPU-bound work. Here, it would be used to call the external API to retrieve the product discount information.
>
> **Client** - serve as the entry point for starting and managing orchestrations. Client functions initiate orchestrator functions and can query or terminate them as needed.
>
> **Entity** - Manage stateful objects in a Durable Function application. Entity functions encapsulate state and provide methods to modify it, making them useful for scenarios where small amounts of state need to be managed over time without an orchestrator.
 
- https://chatgpt.com/share/67319628-3cac-8000-b198-d91005d5c57c

---

### Q076
**You are authoring a set of nested Azure Resource Manager templates to deploy multiple Azure resources.  
The templates must be tested before deployment and must follow recommended practices.  
You need to validate and test the templates before deployment.  
Which tools should you use?**

**Requirements:**

- **Determine whether the templates follow recommended practices.**
    - Parameter file
    - Template function
    - [Azure Resource Manager test toolkit](#q076)
    - User-defined function
    - What-if operation
    - Azure Deployment Manager
  
- **Test and validate changes that templates will make to the environment.**
    - Parameter file
    - Template function
    - Azure Resource Manager test toolkit
    - User-defined function
    - [What-if operation](#q076)
    - Azure Deployment Manager

> **Parameter file** - This is a JSON file that contains parameter values for the ARM template. It allows you to separate the values used in a deployment from the template itself, making it easy to reuse the same template with different configurations. 
>
> **Template function** - These are built-in functions within ARM templates that allow you to perform tasks like string manipulation, resource ID retrieval, and mathematical calculations directly within the template.  
>
> **Azure Resource Manager test toolkit** - The Azure Resource Manager Test Toolkit (also known as ARM TTK) is a command-line tool that evaluates ARM templates against Azure's best practices. It checks for common mistakes, misconfigurations, and adherence to Azure standards.
>
> **User-defined function** - These are custom functions that can be defined within ARM templates to encapsulate reusable logic, similar to a function in programming. These are written in JSON syntax and can perform calculations or generate complex expressions.
>
> **What-if operation** - The `What-if` operation is an ARM template feature that allows you to see a preview of the changes that a deployment would make to your Azure environment, such as adding, modifying, or deleting resources.
>
> **Azure Deployment Manager** - Azure Deployment Manager (ADM) is a tool for orchestrating complex multi-step deployments in Azure. It allows you to deploy ARM templates in a phased approach, often useful for coordinating large deployments across multiple regions or services.

- https://chatgpt.com/share/67319a14-27c8-8000-82d2-d90e1f0b588f
- https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/test-toolkit
- https://learn.microsoft.com/en-us/azure/azure-resource-manager/templates/deploy-what-if?tabs=azure-powershell

---

### Q077
**You develop Azure Durable Functions to manage vehicle loans.   
The loan process includes multiple actions that must be run in a specified order. One of the actions includes a customer credit check process, which may require multiple days to process.  
You need to implement Azure Durable Functions for the loan process.  
Which Azure Durable Functions type should you use?**

- [orchestrator](#q077)
- client
- entity
- activity

> **Orchestrator function:** This is used to define the workflow or sequence of tasks in Durable Functions. It manages the order of operations and handles long-running processes, such as waiting for a customer credit check, which can take multiple days. The orchestrator function can pause and resume as needed, allowing for delays like waiting for external actions (e.g., credit check results) to complete.
>
> **Client function:** The client function initiates the orchestration but does not manage the workflow itself. It triggers the orchestration and returns control to the caller after starting the process.
>
> **Entity function:** This is used for managing stateful entities that maintain state over time but are not suitable for orchestrating workflows involving multiple tasks.
>
> **Activity function:** Activity functions are the tasks that are executed as part of the orchestration. They perform the actual work (such as checking the credit score), but they cannot manage the flow or ordering of tasks.

- https://chatgpt.com/share/6731a000-a700-8000-b43c-2e8e766dd062

---

### Q078
**You are developing an Azure Function app.  
All functions in the app meet the following requirements:  
• Run until either a successful run or until 10 run attempts occur.  
• Ensure that there are at least 20 seconds between attempts for up to 15 minutes.  
You need to configure the `host.json` file.  
How should you complete the code segment?**

```
{
    "SLOT_1": {
        "strategy": "SLOT_2",
        "SLOT_3": 10,
        "minimumInterval": "00:00:20",
        "maximumInterval": "00:15:00"
    }
}
```

- SLOT_1
    - [retry](#q078)
    - healthMonitor
    - singleton

- SLOT_2
    - [exponentialBackoff](#q078)
    - counterThreshold
    - fixedDelay

- SLOT_3
    - [maxRetryCount](#q078)
    - healthCheckInterval
    - healthCheckThreshold


> **Exponential backoff** retry strategy is a technique for retrying failed operations in a manner that avoids overloading the system being accessed. It works by increasing the amount of time that is waited between each retry attempt, using an exponential function to calculate the wait time.  
> For exponential backoff `minimumInterval`/`maxInterval` are used. For fixed delay `delayInterval` is used

- https://learn.microsoft.com/en-us/azure/azure-functions/functions-bindings-error-pages?tabs=exponential-backoff%2Cisolated-process%2Cnode-v4%2Cpython-v2&pivots=programming-language-csharp#retry-strategies

---

### Q079
**You develop Azure Web Apps for a commercial diving company. Regulations require that all divers fill out a health questionnaire every 15 days after each diving job starts.  
You need to configure the Azure Web Apps so that the instance count scales up when divers are filling out the questionnaire and scales down after they are complete.  
You need to configure autoscaling.  
What are two possible auto scaling configurations to achieve this goal?**

- Recurrence profile
- [CPU usage-based autoscaling](#q079)
- Fixed date profile
- [Predictive autoscaling](#q079)

> **Recurrence Profile:** This auto-scaling option allows you to define a set schedule when scaling actions should occur. For instance, you can configure your app to scale up during high-demand periods (e.g., weekdays during business hours) and scale down during off-peak hours (e.g., weekends or late nights). This is useful for predictable traffic patterns.  
>
> **CPU Usage-Based Autoscaling:** This option scales the number of instances based on the CPU usage of the app service. You can set thresholds for CPU utilization, and the system will automatically adjust the number of instances to maintain optimal performance. For example, you can configure scaling to occur when CPU usage exceeds 70% for a specific period.  
>
> **Fixed Date Profile:** With this auto-scaling option, scaling actions are based on specific fixed dates (e.g., a particular day of the week or a calendar date). You can use this option to adjust resources based on known events or seasons, like scaling up during the holiday season or a marketing campaign.
>
> **Predictive Autoscaling:** Predictive autoscaling uses machine learning algorithms to analyze historical traffic patterns and predict future resource requirements. Based on these predictions, it automatically adjusts the number of instances before the demand spike occurs, minimizing delays in scaling.

- https://chatgpt.com/share/6731ca94-a2ac-8000-9e60-d76aca50de05
- https://learn.microsoft.com/en-us/azure/azure-monitor/autoscale/autoscale-overview
- https://learn.microsoft.com/en-us/azure/azure-monitor/autoscale/autoscale-predictive
- https://learn.microsoft.com/en-us/azure/azure-monitor/autoscale/autoscale-multiprofile?tabs=templates

---

### Q080
**You are developing an online game that allows players to vote for their favorite photo that illustrates a word. The game is built by using Azure Functions and uses durable entities to track the vote count.  
The voting window is 30 seconds. You must minimize latency.  
You need to implement the Azure Function for voting.  
How should you complete the code?**
```
[FunctionName ("Vote" )]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger("POST", Route="pic/{id}")] HttpRequestMessage req,
    SLOT_1 c,
    string id
){
    var eid = new EntityId("pic", id);
    await c.SLOT_2(eid, "vote");
    return req.CreateResponse(HttpStatusCode.OK);
}
```

- SLOT_1
    - CallEntityAsync
    - SignalEntityAsync
    - [[DurableClient] IDurableEntityClient](#q080)
    - [DurableClient] IDurableOrchestrationClient

- SLOT_2
    - CallEntityAsync
    - [SignalEntityAsync](#q080)
    - [DurableClient] IDurableEntityClient
    - [DurableClient] IDurableOrchestrationClient


> **SLOT_1:**   
> `[DurableClient] IDurableEntityClient` provides access to durable entities, which is needed to interact with the voting entity.  
> `[DurableClient] IDurableOrchestrationClient` is an attribute that binds the function to an orchestration client, which is used for starting, managing, and querying orchestrations.  
>  An orchestration client is used for handling orchestrations (multi-step workflows) and is not intended for direct interaction with durable entities. Thus, this is not suitable for SLOT_1 because we need an entity client, not an orchestration client.
>
> **SLOT_2:**
> `CallEntityAsync` invokes an operation on a durable entity and waits for it to complete, returning a response.  Although it could be used to perform the voting operation, it would add latency by waiting for each response.  
> `SignalEntityAsync` is an asynchronous, **one-way operation** that sends a signal to a durable entity without waiting for the response. This is ideal for actions like voting where the function does not need to wait for the entity's response to continue processing.

```csharp
//completed code
[FunctionName("Vote")]
public static async Task<HttpResponseMessage> Run(
    [HttpTrigger("POST", Route="pic/{id}")] HttpRequestMessage req,
    [DurableClient] IDurableEntityClient c,
    string id
){
    var eid = new EntityId("pic", id);
    await c.SignalEntityAsync(eid, "vote");
    return req.CreateResponse(HttpStatusCode.OK);
}
```

- https://chatgpt.com/share/6731dc5e-2114-8000-b67b-ceda959b4777
  
---

### Q081
**You have an App Service plan named asp1 based on the Free pricing tier.  
You plan to use asp1 to implement an Azure Function app with a queue trigger. Your solution must minimize cost.  
You need to identify the configuration options that will meet the requirements.  
Which value should you configure?**

**Configuration Option:**

- **Azure App Service Feature**
    - [Always On](#q081)
    - Managed Identity
    - Continuous Deployment

- **Azure App Service pricing tier**
    - [Basic](#q081)
    - Shared
    - Standard

> **Always On** - Required for non-Consumption plans to keep the function app running continuously, which is crucial if you move to a dedicated plan.  
> **Free** and **Shared** tier App Service plans aren't supported by Azure Functions. To ensure the function runs continuously and can handle queue triggers effectively, you should choose at least the **Basic** tier or higher. The **Basic** tier provides dedicated resources at minimal cost.

- https://chatgpt.com/share/6731ec22-bef0-8000-ab96-5a6923f1a342
- https://learn.microsoft.com/en-us/azure/azure-functions/dedicated-plan

---

### Q082
**You are developing several microservices to run on Azure Container Apps.  
The microservices must allow HTTPS access by using a custom domain.  
You need to configure the custom domain in Azure Container Apps.  
In which order should you perform the actions?**

- Validate the custom domain name.
- Enable ingress.
- Bind the certificate.
- Add DNS records to the domain provider.
- Add the custom domain name.

> 1. Enable ingress
> 2. Add the custom domain name
> 3. Bind the certificate
> 4. Add DNS records to the domain provider
> 5. Validate the custom domain name

- https://learn.microsoft.com/en-us/azure/container-apps/custom-domains-certificates

---

### Q083
**You are developing several microservices to run on Azure Container Apps. External HTTP ingress traffic has been enabled for the microservices.  
The microservices must be deployed to the same virtual network and write logs to the same Log Analytics workspace.  
You need to deploy the microservices.  
What should you do?**

- Enable single revision mode.
- Use a separate environment for each container.
- Use a private container registry image and single image for all containers.
- [Use a single environment for all containers.](#q083)
- Enable multiple revision mode.

> When deploying multiple microservices to Azure Container Apps that need to be on the same virtual network and write logs to the same Log Analytics workspace, using a **single environment** for all containers is the best choice. In Azure Container Apps, an environment provides the shared network boundary, allowing all container apps within the same environment to communicate over a virtual network if configured. Additionally, a single environment enables centralized log collection in a single Log Analytics workspace, as logging settings are configured at the environment level.
>
> **Enable single revision mode:**  
> In Azure Container Apps, revision modes control how updates to the application are managed. Single revision mode means only one version of the container app is active at a time, which simplifies traffic management because updates automatically replace the existing version.  
>  While this mode can be useful for controlling app updates, it does not impact networking, logging, or deployment to the same virtual network. Therefore, it does not help fulfill the requirements of shared logging or network configuration.
>
> **Use a separate environment for each container:**  
> Each environment in Azure Container Apps serves as a separate network and logging boundary. If you deploy each container app in its own environment, each would be isolated in its own virtual network configuration, and logging would also be separate.
>
> **Use a private container registry image and single image for all containers:**  
> While using a private registry is recommended for security, this does not relate to network configuration or shared logging. Also, microservices are typically deployed as separate images to maintain independent functionality, so using a single image is generally unnecessary and unrelated to the requirements. 
>
> **Enable multiple revision mode:**    
> Multiple revision mode allows multiple versions (revisions) of a container app to run simultaneously, with traffic split across revisions according to the configuration. This is useful for A/B testing, gradual rollout, or canary deployments.  
> While helpful for deployment strategies, multiple revision mode does not address network or logging requirements and is irrelevant to this scenario.

- https://chatgpt.com/share/6731f168-aa28-8000-b2cc-80359bdfd702
- https://learn.microsoft.com/en-us/azure/container-apps/environment

---

### Q084
**You are developing several microservices to run on Azure Container Apps. External HTTP ingress traffic has been enabled for the microservices.  
A deployed microservice must be updated to allow users to test new features. You have the following requirements:  
• Enable and maintain a single URL for the updated microservice to provide to test users.  
• Update the microservice that corresponds to the current microservice version.  
You need to configure Azure Container Apps.  
Which features should you configure?**

**Requirements:**
- Single URL for test users
    - [Revision label](#q084)
    - Revision mode
    - Container image
    - Container registry

- Current microservice activation
    - Revision label
    - [Revision mode](#q084)
    - Container image
    - Container registry

> **Revision Label:** For container apps with external HTTP traffic, labels are a portable means to direct traffic to specific revisions. A label provides a unique URL that you can use to route traffic to the revision that the label is assigned.
>
> **Revision Mode:** The revision mode controls whether only a single revision or multiple revisions of your container app can be simultaneously active.

- https://learn.microsoft.com/en-us/azure/container-apps/revisions

---

### Q085
**You plan to develop an Azure Functions app with an HTTP trigger.  
The app must support the following requirements:  
• Event-driven scaling  
• Ability to use custom Linux images for function execution  
You need to identify the app's hosting plan and the maximum amount of time that the app function can take to respond to incoming requests.  
Which configuration setting values should you use?**

**Configuration Settings:**

- **Hosting Plan**
    - Consumption
    - Dedicated
    - [Premium](#q085)

- **Timeout Value**
    - [230 seconds](#q085)
    - 10 minutes
    - unlimited

> **Event-driven scaling:** The **Consumption** and **Premium** plans support automatic scaling based on events, while the **Dedicated** plan does not.  
> **Custom Linux images:** Only the **Premium** plan supports using custom container images, including custom Linux images. The **Consumption** and **Dedicated** plans do not support this feature.  
>
> **Timeout requirements:** The **Premium** plan supports a configurable timeout, which can be set to a maximum of **unlimited**. However, Regardless of the function app timeout setting, **230 seconds** is the maximum amount of time that an HTTP triggered function can take to respond to a request.  

- https://learn.microsoft.com/en-us/azure/azure-functions/functions-scale#overview-of-plans
- https://learn.microsoft.com/en-us/azure/azure-functions/functions-scale#scale
- https://learn.microsoft.com/en-us/azure/azure-functions/functions-scale#timeout

---

### Q086
**You develop a Python application for image rendering. The application uses GPU resources to optimize rendering processes.  
You have the following requirements:  
• The application must be deployed to a Linux container.  
• The container must be stopped when the image rendering is complete.  
• The solution must minimize cost.  
You need to deploy the application to Azure.**

- **Compute target**
    - [Azure Container Instances](#q086)
    - Azure Kubernetes Service
    - Azure Container Apps
    - Azure App Service

> **Azure Container Instances (ACI):** ACI is a good choice for running containers without managing infrastructure and provides a cost-effective, serverless compute option that allows GPU usage. Since you want the container to be stopped when the image rendering is complete to minimize cost, you can use the "Single" container group mode in Azure Container Instances. This mode is suitable for scenarios where you want to run a single container task and stop it when it's done.

- **Container termination**
    - [Restart Policy](#q086)
    - Environment Variables
    - System-Assigned Managed Identity
    - User-Assigned Managed Identity

> **Restart Policy:** The restart policy in ACI can be set to `OnFailure` or `Never`, which enables the container to stop once the image rendering job is done. Using the `Never` policy ensures that the container will not restart after the task completes, helping to control costs.

- https://chatgpt.com/share/67324bf8-0930-8000-99ce-199f1d0f4979
- https://learn.microsoft.com/en-gb/azure/container-instances/container-instances-overview
- https://learn.microsoft.com/en-us/azure/container-instances/container-instances-gpu
- https://learn.microsoft.com/en-us/azure/container-instances/container-instances-restart-policy

---

### Q087
**You plan to develop an Azure Functions app with an Azure Blob Storage trigger. The app will be used infrequently, with a limited duration of individual executions.  
The app must meet the following requirements:  
• Event-driven scaling  
• Support for deployment slots  
• Minimize costs  
You need to identify the hosting plan and the maximum duration when executing the app.  
Which configuration setting values should you use?**

**Configuration Settings:**

- **Hosting Plan**
    - [Consumption](#q087)
    - Dedicated
    - Premium

- **Maximum Execution Time**
    - 230 seconds
    - [10 minutes](#q087)
    - unlimited


> The **Consumption plan** is suitable because it provides event-driven scaling, supports deployment 2 slots, minimizes costs for infrequent usage.  
> **Maximum Execution Time: 10 minutes** (the maximum execution time on the Consumption plan is up to 5 minutes by default, but this can be increased to 10 minutes in configuration).

- https://learn.microsoft.com/en-us/azure/azure-functions/functions-scale#service-limits

---

### Q088
**You are developing an ASP.NET Core app hosted in Azure App Service.  
The app requires custom claims to be returned from Microsoft Entra ID for user authorization. The claims must be removed when the app registration is removed.  
You need to include the custom claims in the user access token.  
What should you do?**

- Require the https://graph.microsoft.com/.default scope during authentication.
- Configure the app to use the OAuth 2.0 authorization code flow.
- Implement custom middleware to retrieve role information from Azure AD.
- Add the groups to the `groupMembershipClaims` attribute in the app manifest.
- [Add the roles to the `appRoles` attribute in the app manifest.](#q088)
  
> **Require the https://graph.microsoft.com/.default scope during authentication**  
> The https://graph.microsoft.com/.default scope is used to request permissions to access the Microsoft Graph API on behalf of the signed-in user. It provides access to a broad set of data within Microsoft 365, such as user profiles, files, or email. However, this does not add custom claims to the access token for the app itself.
>
> **Configure the app to use the OAuth 2.0 authorization code flow**  
> The OAuth 2.0 authorization code flow is a standard authentication flow used for securely obtaining access tokens and ID tokens in web applications. This flow allows the app to authenticate users and obtain tokens that can be used to access resources. Although the authorization code flow is essential for authenticating users, it does not add custom claims to the tokens. 
>
> **Implement custom middleware to retrieve role information from Azure AD**  
> sing middleware to retrieve role information would add unnecessary complexity and potentially require extra API calls to Microsoft Graph. It doesn't add custom claims directly to the token; instead, it fetches information dynamically, which isn't as efficient or secure as embedding claims directly in the token.
>
> **Add the groups to the `groupMembershipClaims` attribute in the app manifest**  
> The `groupMembershipClaims` attribute in the app manifest allows Microsoft Entra ID to include group memberships in the token. When enabled, the token may include group IDs, or links to group memberships if there are many groups. This attribute is useful if your app needs to check a user's group memberships, but it's limited to groups and does not support custom claims. 
>
> **Add the roles to the `appRoles` attribute in the app manifest**  
> The `appRoles` attribute in the app manifest allows you to define custom roles or claims for the app. These roles can be assigned to users or service principals and are automatically included in the access token when users authenticate. This is particularly useful for custom claims needed for user authorization. Adding custom roles in the appRoles attribute is a straightforward way to define custom claims, which will be automatically included in the token. It also ensures these roles and claims are removed if the app registration is deleted, meeting all requirements.

- https://chatgpt.com/share/673251cb-c0e0-8000-b6fc-2fa7d6e81266
- https://learn.microsoft.com/en-us/entra/identity-platform/howto-add-app-roles-in-apps
- https://learn.microsoft.com/en-us/entra/identity-platform/reference-app-manifest

---

### Q089
**You are developing a microservice to run on Azure Container Apps for a company. External HTTP ingress traffic has been enabled.  
The company requires that updates to the microservice must not cause downtime.  
You need to deploy an update to the microservices.  
What should you do?**

- [Enable single revision mode.](#q089)
- Use multiple environments for each container.
- Use a private container registry and single image for all containers.
- Use a single environment for all containers.
- Enable multiple revision mode.

> In **single revision mode**, Container Apps ensures your app doesn't experience downtime when creating a new revision. The existing active revision isn't deactivated until the new revision is ready.  
> A new revision is considered ready when:  
> - The revision has provisioned successfully  
> - The revision has scaled up to match the previous revisions replica count (respecting the new revision's min and max replica count)  
> - All the replicas have passed their startup and readiness probes  

- https://learn.microsoft.com/en-us/azure/container-apps/revisions#zero-downtime-deployment

---

### Q090
**A company uses Azure Container Apps. A container app named App1 resides in a resource group named RG1.  
The company requires testing of updates to App1.  
You enable multiple revision modes on App1.  
You need to ensure traffic is routed to each revision of App1.  
How should you complete the code segment?**
```
az SLOT_1 SLOT_2 traffic set
--name App1
--resource-group RG1
--revision-weight <REVISION_1>=80 <REVISION_2>=20
```

- SLOT_1
    - container
    - [containerapp](#q090)
    - network
    - resource
  
- SLOT_2
    - app
    - connection
    - [ingress](#q090)
    - revision

> You can configure traffic splitting between revisions using the `az containerapp ingress traffic set` command. You can specify the revisions by name with the `--revision-weight` parameter or by revision label with the `--label-weight` parameter.  
```bash
az containerapp ingress traffic set
--name APP_NAME
--resource-group RESOURCE_GROUP
--revision-weight LABEL_1=80 LABEL_2=20
```

> https://learn.microsoft.com/en-us/azure/container-apps/traffic-splitting?pivots=azure-cli

---

### Q091
**You deploy an Azure Container Apps app and disable ingress on the container app.  
Users report that they are unable to access the container app. You investigate and observe that the app has scaled to 0 instances.  
You need to resolve the issue with the container app.  
Solution: Enable ingress, create an HTTP scale rule, and apply the rule to the container app.  
Does the solution meet the goal?**

- Yes
- [No](#q091)

> The HTTP scale rule in Azure App Service allows you to automatically scale your app based on HTTP traffic. However, if the Azure container app is scaled down to 0 instances, the HTTP scale rule will not work because there are no instances to scale.   
> In other words, the HTTP scale rule only applies when there are active instances of the app to handle incoming HTTP requests. When the app is scaled down to 0 instances, no requests are being processed, and the scale rule does not have any effect.  
> So to address this first, we need to ensure that there is at least one instance of the container app running to handle incoming requests. This may involve adjusting the scaling settings, configuring minimum instance limits, or implementing a health check mechanism to keep at least one instance running at all times, even during periods of low traffic.  

- https://learn.microsoft.com/en-us/azure/container-apps/scale-app?pivots=azure-cli#default-scale-rule

---

### Q092
**You deploy an Azure Container Apps app and disable ingress on the container app.  
Users report that they are unable to access the container app. You investigate and observe that the app has scaled to 0 instances.  
You need to resolve the issue with the container app.  
Solution: Enable ingress, create a custom scale rule, and apply the rule to the container app.  
Does the solution meet the goal?**

- Yes
- [No](#q092)

> Make sure you create a scale rule or set `minReplicas` to 1 or more if you don't enable ingress. If ingress is disabled and you don't define a `minReplicas` or a "custom scale rule", then your container app will scale to zero and have no way of starting back up.  

- https://learn.microsoft.com/en-us/azure/container-apps/scale-app?pivots=azure-cli#custom

---

### Q093
**You deploy an Azure Container Apps app and disable ingress on the container app.  
Users report that they are unable to access the container app. You investigate and observe that the app has scaled to 0 instances.  
You need to resolve the issue with the container app.  
Solution: Enable ingress and configure the minimum replicas to 1 for the container app.  
Does the solution meet the goal?**

- [Yes](#q093)
- No

> **Ingress Disabled:** When ingress is disabled, the container app cannot receive external traffic, which prevents users from accessing it. Enabling ingress allows external traffic to reach the app.  
> **Scaling to 0 Instances:** By configuring the minimum replicas to 1, the app will maintain at least one active instance, even when idle, which prevents it from scaling down to 0 and becoming inaccessible.

- https://chatgpt.com/share/673321e8-8634-8000-a4d0-097d067c770f

---

### Q094 - Case study
**<u>Background:</u>  
Munsons Pickles and Preserves Farm is an agricultural cooperative corporation based in Washington, US, with farms located across the United States.  
The company supports agricultural production resources by distributing seeds fertilizers, chemicals, fuel, and farm machinery to the farms.**  

**<u>Current Environment:</u>  
The company is migrating all applications from an on-premises datacenter to Microsoft Azure.  
Applications support distributors, farmers, and internal company staff.**

**<u>Corporate website:</u>  
The company hosts a public website located at http://www.munsonspicklesandpreservesfarm.com. The site supports farmers and distributors who request agricultural production resources.**

**<u>Farms:</u>     
The company created a new customer tenant in the Microsoft Entra admin center to support authentication and authorization for applications.**

**<u>Distributors:</u>     
Distributors integrate their applications with data that is accessible by using APIs hosted at http://www.munsonspicklesandpreservesfarm.com/api to receive and update resource data.**

**The application components must meet the following requirements:**
- **Corporate website:**
    - **The site must be migrated to Azure App Service.**
    - **Costs must be minimized when hosting in Azure.**
    - **Applications must automatically scale independent of the compute resources.**
    - **All code changes must be validated by internal staff before release to production.**
    - **File transfer speeds must improve, and webpage-load performance must increase.**
    - **All site settings must be centrally stored, secured without using secrets, and encrypted at rest and in transit.**
    - **A queue-based load leveling pattern must be implemented by using Azure Service Bus queues to support high volumes of website agricultural production resource requests.**
- **Farms:**
    - **Farmers must authenticate to applications by using Microsoft Entra ID.**
- **Distributors:**
    - **The company must track a custom telemetry value with each API call and monitor performance of all APIs.**
    - **API telemetry values must be charted to evaluate variations and trends for resource data.**
- **Internal staff:**
    - **App and API updates must be validated before release to production.**
    - **Staff must be able to select a link to direct them back to the production app when validating an app or API update.**
    - **Staff profile photos and email must be displayed on the website once they authenticate to applications by using their Microsoft Entra ID.**
- **Security**
    - **All web communications must be secured by using TLS/HTTPS.**
    - **Web content must be restricted by country/region to support corporate compliance standards.**
    - **The principle of least privilege must be applied when providing any user rights or process access rights.**
    - **Managed identities for Azure resources must be used to authenticate services that support Microsoft Entra ID authentication.**

**Issues:**
- **Corporate website:**
    - **Farmers report HTTP 503 errors at the same time as internal staff report that CPU and memory usage are high.**
    - **Distributors report HTTP 502 errors at the same time as internal staff report that average response times and networking traffic are high.**
    - **Internal staff report webpage load sizes are large and take a long time to load.**
    - **Developers receive authentication errors to Service Bus when they debug locally.**
- **Distributors:**
    - **Many API telemetry values are sent in a short period of time. Telemetry traffic, data costs, and storage costs must be reduced while preserving a statistically correct analysis of the data points sent by the APIs.**

**You need to configure App Service to support the corporate website migration.  
Which configuration should you use?**

- App Service Plan
    - Basic
    - [Standard](#q094)
    - Premium
    - Isolated

> **Standard:** It meets the need for auto-scaling and cost efficiency while providing the necessary features such as SSL and custom domains.

- Code change validation feature
    - [Deployment slot](#q094)
    - Custom container
    - Domain certificate
    - Deployment credentials

> **Deployment Slot:** Enables the company to validate all code changes in a pre-production environment, ensuring stability and performance before changes are made live.

---

### Q095
**You have an Azure Cosmos DB for NoSQL API account named account1 and a database named `db1`. An application named `app1` will access `db1` to perform read and write operations.  
You plan to modify the consistency levels for read and write operations performed by `app1` on `db1`.  
You must enforce the consistency level on a per-operation basis whenever possible.  
You need to configure the consistency level for read and write operations.  
Which locations should you configure?**

- Read Opetation:
    - [app1](#q095)
    - db1
    - account1

- Write Operation:
    - [app1](#q095)
    - db1
    - account1

> **Per-operation consistency** means that you can set the consistency level for each individual read or write operation within your application code, instead of having a single, global consistency level for the entire database. This allows you to fine-tune consistency based on the specific needs of different parts of your application, overriding the default consistency level set at the account or database level when necessary.    
> This feature is typically managed through the database client library, where you specify the desired consistency level for each query or write operation within your application code.  
>  
> **Account level (`account1`):** The default consistency level for the entire Cosmos DB account can be set here. However, this is a default and cannot be overridden on a per-operation basis once set.  
> **Database level (`db1`):** Cosmos DB does not support setting the consistency level at the database level.  
> **Client level (`app1`):** For per-operation consistency, you need to specify it within the application code, which allows you to override the default consistency level for specific read and write operations.

- https://chatgpt.com/share/67346fd7-6118-8000-b3ea-e2aa9306ad3d
- https://learn.microsoft.com/en-us/azure/cosmos-db/nosql/how-to-manage-consistency#override-the-default-consistency-level

---

### Q096
**You are creating an Azure Functions app project in your local development environment by using Azure Functions Core Tools.  
You must create the project in either Python or C# without using a template.  
You need to specify the command and its parameter required to create the Azure Functions app project.  
Which command and parameter should you specify?**

**Syntax Element**
- Command
    - func new
    - [func init](#q096)
    - func azure

>**`func new`:** This command is used to create a new function within an existing Azure Functions project. It prompts for the function template type (e.g., HTTP trigger, Queue trigger) and other relevant details.  
It does not initialize a new project but rather adds functions to an existing one.  
>
>**`func init`:** This command is used to initialize a new Azure Functions project in the specified language and runtime environment.  
This is the correct command when creating a new Functions project, as it sets up the necessary project files and folders.  
>
>**`func azure`:** This is not a valid command in Azure Functions Core Tools. It’s not used to create or configure Azure Functions projects or functions.

- Parameter
    - --language
    - [--worker-runtime](#q096)
    - --taget-framework

>**`--language`:** Used primarily when the runtime supports multiple languages; often optional, especially when there’s only one language option for a given runtime. e.g. `func init MyFunctionApp --worker-runtime node --language typescript`.  
>
>**`--worker-runtime`:** Specifies the runtime stack for the Azure Functions app project. Sets up the project structure with configuration files that target the specified runtime, allowing the Azure Functions host to manage execution in that environment.  
> Accepts values such as `dotnet`, `python`, `node`, `java`, `powershell`, etc., depending on the runtime environment you need.
>
> **`--target-framework`:** Specifies the target framework for the project. This is used in .NET projects to specify the version of the .NET framework to target. It is not typically used in Python projects.

- https://chatgpt.com/share/67347897-6914-8000-bf1d-ee1b99965165
- https://learn.microsoft.com/en-us/azure/azure-functions/functions-core-tools-reference?tabs=v2#func-init

---

### Q097
**You have an Azure App Service plan named APSPlan1 set to the Basic B1 pricing tier. APSPlan1 contains an App Service web app named WebApp1.  
You plan to enable schedule-based autoscaling for APSPlan1.  
You need to minimize the cost of running WebApp1.  
Solution: Scale up ASPPlan1 to the Premium V2 pricing tier.  
Does the solution meet the goal?**

- Yes
- [No](#q097)

> Scaling up `APSPlan1` to the `Premium V2` pricing tier would increase costs rather than minimize them. To enable schedule-based autoscaling while minimizing costs, it would be more cost-effective to consider scaling within the Basic tier if possible or to select the **`Standard`** tier, which supports autoscaling without the additional expense associated with Premium V2.

- https://chatgpt.com/share/67348248-eacc-8000-9174-26bbfb7c08e4

---

### Q098
**You are developing a solution that uses the Azure Storage Client library for .NET. You have the following code: (Line numbers are included for reference only.)**
```csharp
01    CloudBlockBlob src = null;
02    try 
03    {
04        src = container.ListBlobs().OfType<CloudBlockBlob>().FirstOrDefault();
05        var id = await src.AcquireLeaseAsync(null);
06        var dst = container.GetBlockBlobReference(src.Name);
07        string cpid = await dst.StartCopyAsync(src);
08        await dst.FetchAttributeAsync () ;
09        return id;
10    }
11    catch (Exception e)
12    {
13        throw;
14    }
15    finally
16    {
17       if(src != null)
18            await src. FetchAttributesAsync () ;
19        if (src.Properties.LeaseState != LeaseState.Available)
20            await src.BreakLeaseAsync(new TimeSpan(0)) ;
21    }
```
**For each of the following statements, select Yes if the statement is true. Otherwise, select No.**

- The code creates an infinite lease
    - [Yes](#q098)
    - No
>  In line 05, the code calls `src.AcquireLeaseAsync(null);`. Passing `null` as the lease duration creates an infinite lease. Otherwise, this must be `TimeSpan` of 15 to 60 seconds.  An infinite lease has no expiration until it is explicitly released or broken.  

- The code at line 06 always creates a new blob
    - Yes
    - [No](#q098)
> Line 06 retrieves a reference to an existing blob with `container.GetBlockBlobReference(src.Name);`. This method does not create a new blob; it simply creates a reference to the blob, allowing further operations. The blob is only created if data is uploaded to it.  

- The finally block releases the lease
    - [Yes](#q098)
    - No
> In the finally block, lines 17-20 check if `src` has an active lease. If the lease state is not `LeaseState.Available`, line 20 attempts to break the lease using `src.BreakLeaseAsync(new TimeSpan(0));`. This operation effectively releases the lease.

-https://chatgpt.com/share/673498d5-3adc-8000-b938-3747012e16cd

---

### Q099
**You are building a website that uses Azure Blob storage for data storage. You configure Azure Blob storage lifecycle to move all blobs to the archive tier after 30 days.    
Customers have requested a service-level agreement (SLA) for viewing data older than 30 days.  
You need to document the minimum SLA for data recovery.  
Which SLA should you use?**

- at least two days
- [between one and 15 hours](#q099)
- at least one day
- between zero and 60 minutes

> **Standard priority:** The rehydration request is processed in the order it was received and might take up to 15 hours to complete for objects under 10 GB in size.  
> **High priority:** The rehydration request is prioritized over standard priority requests and might complete in less than one hour for objects under 10 GB in size.

- https://learn.microsoft.com/en-us/azure/storage/blobs/archive-rehydrate-overview#rehydration-priority

---

### Q100
**You are developing a ticket reservation system for an airline.  
The storage solution for the application must meet the following requirements:  
• Ensure at least 99.99% availability and provide low latency.  
• Accept reservations even when localized network outages or other unforeseen failures occur.  
• Process reservations in the exact sequence as reservations are submitted to minimize overbooking or selling the same seat to multiple travelers.  
• Allow simultaneous and out-of-order reservations with a maximum five-second tolerance window.  
You provision a resource group named airlineResourceGroup in the Azure South-Central US region.  
You need to provision a SQL API Cosmos DB account to support the app.  
How should you complete the Azure CLI commands?**
```
resourceGroupName='airlineResourceGroup'
name='docdb-airline-reservations'
databaseName='docdb-tickets-database'
collectionName='docdb-tickets-collection'
consistencyLevel=SLOT_1

az cosmosdb create
--name $name
SLOT_2
--resource-group $resourceGroupName
--max-interval 5
SLOT_3
--default-consistency-level $consistencyLevel
```

- SLOT_1
    - Strong
    - Eventual
    - ConsistentPrefix
    - [BoundedStaleness](#q100)

- SLOT_2
    - --enable-virtual-network true
    - --[enable-automatic-failover true](#q100)
    - --kind 'GlobalDocumentDB'
    - --kind 'MongoDB'
- SLOT_3
    - --locations 'southcentralus'
    - --locations 'eastus'
    - [--locations 'southcentralus=0 eastus=1 westus=2'](#q100)
    - --locations 'southcentralus=0'

> **BoundedStaleness:** The reads are guaranteed to honor the consistent-prefix guarantee. The reads might lag behind writes by at most "K" versions (that is, "updates") of an item or by "T" time interval. 
>
> For multi-region Cosmos accounts that are configured with a single-write region, enable automatic-failover by using Azure CLI or Azure portal.
After you **enable automatic failover**, whenever there is a regional disaster, Cosmos DB will automatically failover your account.
>
> Need multi-region to accept reservations even when localized network outages or other unforeseen failures occur.  
> `--locations'southcentralus=0 eastus=1 westus=2` Specifies the regions for Cosmos DB to distribute data, along with the priority order in case of a failover. Each region is assigned a priority (0, 1, 2, etc.), where 0 is the primary region. Cosmos DB will use `southcentralus` as the primary write region (0) and will automatically fail over to eastus (1) if `southcentralus` is unavailable.

- https://chatgpt.com/share/6734ec79-8730-8000-a4bc-b80d500c1864
- https://learn.microsoft.com/en-us/azure/cosmos-db/consistency-levels
- https://learn.microsoft.com/en-us/azure/reliability/reliability-cosmos-db-nosql?toc=%2Fazure%2Fcosmos-db%2Ftoc.json

---

### Q101
**You are preparing to deploy a Python website to an Azure Web App using a container. The solution will use multiple containers in the same container group.  
The Dockerfile that builds the container is as follows:**
```dockerfile
FROM python:3
ADD website.py
CMD ["python", "./website.py"]
```
**You build a container by using the following command. The Azure Container Registry instance named images is a private registry. `docker build -t images.azurecr.io/website:v1.0.0`  
The user name and password for the registry is "admin".  
The Web App must always run the same version of the website regardless of future builds.  
You need to create an Azure Web App to run the website.   
How should you complete the commands?**
```
az configure --defaults web=website
az configure --defaults group=website
az appservice plan create --name websitePlan SLOT_1

az webapp create --plan websitePlan SLOT_2

az webapp config SLOT_3
```

- SLOT_1
    - --Sku SHARED
    - --tags container
    - --sku B1 --hyper-v
    - [--sku B1 --is-linux](#q101)

> The appropriate `SKU is B1 --is-linux` to indicate a Linux-based basic pricing tier. Multi-container groups currently support only Linux containers. For Windows containers, Azure Container Instances only supports deployment of a single container instance. 

- SLOT_2
    - --deployment-source-url images.azurecr.io/website:v1.0.0
    - --deployment-source-url images.azurecr.io/website:latest
    - [--deployment-container-image-name images.azurecr.io/website:v1.0.0](#q101)
    - --deployment-container-image-name images.azurecr.io/website:latest

> This command creates the Web App and specifies the container image that should be deployed. To ensure it runs the exact specified version of the image (`v1.0.0`), we'll use `--deployment-container-image-name images.azurecr.io/website:v1.0.0`.   
> `-deployment-source-url` option in Azure CLI is used to specify a URL for the source code or repository that should be deployed to the Azure Web App. This option points to a location (usually a Git repository or archive file) where Azure can pull the application's code or content directly.

- SLOT_3
    - set -python-version 2.7 --generic-configurations user=admin password=admin
    - set -python-version 3.6 -generic-configurations user=admin password=admin
    - [container set --docker-registry-server-url https://images.azurecr.io -u admin-p admin](#q101)
    - container set --docker-registry-server-url https://images.azurecr.io/website -u admin-p admin

> This command configures the Web App for container deployment by setting the Docker registry URL and providing the admin credentials. The correct command is container set `--docker-registry-server-url https://images.azurecr.io -u admin -p admin`.

- https://chatgpt.com/share/6734f4f7-d800-8000-af3d-10e97a661e49
- https://learn.microsoft.com/en-us/cli/azure/webapp?view=azure-cli-latest#az-webapp-create
- https://learn.microsoft.com/en-us/azure/container-instances/container-instances-container-groups

---

### Q102
**You are developing a back-end Azure App Service that scales based on the number of messages contained in a Service Bus queue.  
A rule already exists to scale up the App Service when the average queue length of unprocessed and valid queue messages is greater than 1000.  
You need to add a new rule that will continuously scale down the App Service as long as the scale up condition is not met.  
How should you configure the Scale rule?**

- Metric Source
    - Storage queue
    - [Service bus queue](#q102)
    - Current resource
    - Storage queue (classic)
> Since the messages are in a Service Bus queue, this is the correct source.

- Metric Name
    - Message count
    - [Active message count](#q102)
> This metric tracks the number of unprocessed and valid queue messages.

- Time grain statistic
    - Total
    - Maximum
    - [Average](#q102)
    - Count
> Using the average ensures you assess the trend over time and smooth out spikes or dips.

- Operator
    - Greater than
    - Greated than or equal to
    - Less than
    - [Less than or equal to](#q102)
> This ensures the scale-down condition triggers when the queue length is consistently low.

- Operation
    - Increase count by
    - Increase count to
    - [Decrease count by](#q102)
    - Decrease count to
> This decreases the App Service instance count gradually, preventing abrupt scale changes.

- https://chatgpt.com/share/673d866b-1e80-8000-b029-c60413c62da6

---

### Q103
**You have an application that uses Azure Blob storage.  
You need to update the metadata of the blobs.  
Which three methods should you use to develop the solution? 
To answer, move the appropriate methods from the list of methods to the answer area and arrange them in the correct order.**

- Metadata.Add
- SetMetadataAsync
- FetchAttributesAsync
- UploadFileStream
- SetPropertiesAsync

> 1. **`FetchAttributesAsync`**  
This retrieves the existing blob properties and metadata. You need this step to get the current metadata before modifying it. For v12 use `GetPropertiesAsync`,
>
>2. **`Metadata.Add`**  
Use this method to add or update the metadata key-value pairs in the blob's metadata collection.
>
> 3. **`SetMetadataAsync`**  
This saves the updated metadata to the blob in Azure Blob Storage.  

- https://chatgpt.com/share/67402757-b054-8000-a767-f82147daf424
- https://learn.microsoft.com/en-us/azure/storage/blobs/storage-blob-properties-metadata?tabs=dotnet#set-and-retrieve-metadata

---

### Q104
**You are developing an Azure solution to collect point-of-sale (POS) device data from 2,000 stores located throughout the world.  
A single device can produce 2 megabytes (MB) of data every 24 hours. Each store location has one to ve devices that send data.   
You must store the device data in Azure Blob storage. Device data must be correlated based on a device identier. Additional stores are expected to open in the future.  
You need to implement a solution to receive the device data.  
Solution: Provision an Azure Event Grid. Congure the machine identier as the partition key and enable capture.  
Does the solution meet the goal?**

- Yes
- [No](#q104)

> Azure Event Grid is not designed for directly ingesting or processing large volumes of data, such as device-generated telemetry. Event Grid is primarily used for event-driven architectures, where it delivers event notifications to subscribers. It does not natively support features like a partition key for data correlation or automatic capture of raw data into Azure Blob Storage.

- https://chatgpt.com/share/67402e19-7bd8-8000-b4ff-7f0f78a640f6
- https://arindam-das.medium.com/demystifying-azures-eventing-services-a-comparison-of-event-hub-event-grid-and-service-bus-d578693dcf16
- https://learn.microsoft.com/en-us/azure/event-hubs/event-hubs-capture-overview

---

### Q105
**A .NET application needs to receive a message each time an Azure virtual machine nishes processing data.  
The messages must NOT persist after being processed by the receiving application.  
You need to implement the .NET object that will receive the messages.  
Which object should you use?**

- [QueueClient](#q105)
- SubscriptionClient
- TopicClient
- CloudQueueClient

> I would say it is about Microsoft.AzureService.Bus.QueueClient as the difference between Azure.Storage.Queues.CloudQueueClient (v12) is just a legacy version of the Azure.Storage.Queues.QueueClient (v11) So the question is really about what kind of queue message tool you should use. And the key word here is that "message must NOT persist after being processed". So correct answer would be Microsoft.AzureService.Bus.QueueClient (A) as it supports "At-Most-Once" (using ReceiveAndDelete receive mode) deliver mode while Azure.Storage.Queues.CloudQueueClient doesn't.

- https://chatgpt.com/share/67405f3f-c0f0-8000-8689-e50e5f2d6e05
- https://learn.microsoft.com/en-us/azure/service-bus-messaging/service-bus-azure-and-service-bus-queues-compared-contrasted#consider-using-service-bus-queues

---

### Q106
**You are maintaining an existing application that uses an Azure Blob GPv1 Premium storage account. Data older than three months is rarely used.  
Data newer than three months must be available immediately. Data older than a year must be saved but does not need to be available immediately.  
You need to congure the account to support a lifecycle management rule that moves blob data to archive storage for data not modied in the last year.  
Which three actions should you perform in sequence? To answer, move the appropriate actions from the list of actions to the answer area and arrange them in the correct order.**

- Upgrade the storage account to GPv2
- Create a new GPv2 Standard account and set its default access tier level to cool
- Change the storage account access tier from hot to cool
- Copy the data to be archived to a Standard GPv2 storage account and then delete the data from the original storage account

> 1. Upgrade the storage account to GPv2
> Object storage data tiering between hot, cool, and archive is supported in Blob Storage and General Purpose v2 (GPv2) accounts. General Purpose v1 (GPv1) accounts don't support tiering. You can easily convert your existing GPv1 or Blob Storage accounts to GPv2 accounts through the Azure portal.  
>
> 2. Create a new GPV2 standard account with default access level to cool
>
> 3. Copy the data to be archived to a Standard GPv2 storage account and then delete the data from the original storage account

- https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-overview
- https://learn.microsoft.com/en-us/azure/storage/common/storage-account-upgrade?tabs=azure-portal

---

### Q107
**You must connect to a No-SQL globally-distributed database by using the .NET API.  
You need to create an object to congure and execute requests in the database.  
Which code segment should you use?**

- new Container(EndpointUri, PrimaryKey);
- new Database(EndpointUri, PrimaryKey);
- [new CosmosClient(EndpointUri, PrimaryKey);](#q107)

> **CosmosClient:** This is the main entry point for interacting with Azure Cosmos DB using the .NET SDK. It allows you to connect to a Cosmos DB account by specifying the `EndpointUri` and `PrimaryKey`.
```csharp
string EndpointUri = "<your-endpoint-uri>";
string PrimaryKey = "<your-primary-key>";

// Initialize the CosmosClient
CosmosClient cosmosClient = new CosmosClient(EndpointUri, PrimaryKey);

```

---

### Q108
**You have an existing Azure storage account that stores large volumes of data across multiple containers.  
You need to copy all data from the existing storage account to a new storage account. The copy process must meet the following requirements:  
• Automate data movement.  
• Minimize user input required to perform the operation.  
• Ensure that the data movement process is recoverable.  
What should you use?**

- [AzCopy](#q108)
- Azure Storage Explorer
- Azure portal
- .NET Storage Client Library

> AzCopy, The Azcopy tool can be used to copy data from one storage account to another. You can use the tool within automation scripts
to ensure the data can be copied automatically.

- https://learn.microsoft.com/en-us/azure/storage/common/storage-use-azcopy-blobs-copy

---

### Q109
**You are developing a web service that will run on Azure virtual machines that use Azure Storage. You congure all virtual machines to use managed identities.  
You have the following requirements:  
• Secret-based authentication mechanisms are not permitted for accessing an Azure Storage account.  
• Must use only Azure Instance Metadata Service endpoints.  
You need to write code to retrieve an access token to access Azure Storage. To answer, drag the appropriate code segments to the correct locations.  

```
var url = "SLOT_1";
var queryString = "...";
var client = new HttpClient();
var response = await client.GetAsync(url + queryString);
var payload = await response.Content.ReadAsStringAsync();
return SLOT_2;
```

- SLOT_1
    - http://localhost:50342/oauth2/token
    - http://169.254.169.254:50432/oauth2/token
    - http://localhost/metadata/identity/oauth2/token
    - [http://169.254.169.254/metadata/identity/oauth2/token](#q109) 
  
- SLOT_2
    - Document.Parse(payload)
    - new MultipartContent (payload)
    - new NetworkCredential("Azure", payload)
    - [JsonConvert. DeserializeObject<Dictionary<string, string>>(payload)](#q109)

> **SLOT_1:** http://169.254.169.254/metadata/identity/oauth2/token  
> The **Azure Instance Metadata Service** provides information about the virtual machine and its identity. The URL  http://169.254.169.254/metadata/identity/oauth2/token    is the endpoint used to request an access token when managed identities are enabled. The metadata path is mandatory for IMDS, and the endpoint only works from the Azure environment.  
>
> **SLOT_2:** JsonConvert.DeserializeObject<Dictionary<string, string>>(payload)  
> The response from the IMDS endpoint is a JSON payload. To extract the access token, the payload must be deserialized into a dictionary or a similar structure. Using `JsonConvert.DeserializeObject<Dictionary<string, string>>(payload)` is the correct way to parse the token from the JSON response.

- https://chatgpt.com/share/67418365-db74-8000-bbc2-0e8f310a68ed
- https://learn.microsoft.com/en-us/entra/identity/managed-identities-azure-resources/how-to-use-vm-token

---

### Q110
**You are developing a new page for a website that uses Azure Cosmos DB for data storage. 
The feature uses documents that have the following format:**  
```
{
    "name": "John",
    "city" : "Seattle"
}
```
**You must display data for the new page in a specic order. You create the following query for the page:**  
```
SELECT *
FROM People p
ORDER BY p. name, p.city DESC
```
**You need to congure a Cosmos DB policy to support the query. How should you congure the policy?**

```
{
    "automatic" : true
    "indexingMode" : "consistent"
    "includedPaths" : [{"path" : "/*"}],
    "excludedPaths" : [],
    "SLOT_1":[
        {"path": "/name", "order": "descending"},
        {"path": "/city", "order": "SLOT_2"}
    ]
}
```

- SLOT_1
  - orderBy
  - sortOrder
  - ascending
  - descending
  - [compositeIndexes](#q110)

- SLOT_2
  - orderBy
  - sortOrder
  - [ascending](#q110)
  - descending
  - compositeIndexes

> The SQL query is equivalent to `SELECT * FROM People p ORDER BY p.name ASC, p.city DESC`.  
> To support the `ORDER BY` clause  with two or more properties in a query, you need to configure **composite indexes** in Azure Cosmos DB. Composite indexes allow efficient sorting on multiple fields.   
> The order of composite index paths (ascending or descending) should also match the order in the `ORDER BY` clause.  
> The composite index also supports an `ORDER BY` clause with the opposite order on all paths.  
> i.e. index on `(A asc, B asc)` works for queries with `ORDER BY` `(A asc, B asc)` and `(A desc, B desc)`. Not working with `ORDER BY` `(A asc, B desc)`, `(A desc, B asc)` or even `(B asc, A asc)`.

- https://learn.microsoft.com/en-us/azure/cosmos-db/index-policy#order-by-queries-on-multiple-properties

---

### Q111
**You are building a traffic monitoring system that monitors traffic along six highways. The system produces time series analysis-based reports for each highway.  
Data from traffic sensors are stored in Azure Event Hub. Traffic data is consumed by four departments.  
Each department has an Azure Web App that displays the time series-based reports and contains a WebJob that processes the incoming data from Event Hub. All Web Apps run on App Service Plans with three instances.  
Data throughput must be maximized. Latency must be minimized.  
You need to implement the Azure Event Hub. Which settings should you use?**

- Number of Partitions
    - 3
    - 4
    - [6](#q111)
    - 12

- Partition Key
    - [Highway](#q111)
    - Department
    - Timestamp
    - VM Name

> The rationale is that since there are 6 highways, partitioning by highway ensures that events related to each highway are processed in order and kept separate. This structure supports scalability and ordered event processing, which is essential for time series analysis in the system.  
> The partition key determines how events are distributed across partitions. Using **"Highway"** as the partition key ensures that all events related to a particular highway are sent to the same partition. This is crucial for maintaining the order of events and for processing highway-specific time series analysis effectively.  

- https://learn.microsoft.com/en-us/azure/event-hubs/event-hubs-features#partitions

---

### Q112
**You are developing a microservices solution. You plan to deploy the solution to a multinode Azure Kubernetes Service (AKS) cluster.  
You need to deploy a solution that includes the following features:  
• reverse proxy capabilities  
• congurable trac routing  
• TLS termination with a custom certicate  
Which components should you use?**  

**Componnts**
- Helm
- Draft
- Brigade
- KubeCtl
- Ingress Controller
- CoreDNS
- Virtual Kubelet

**Actions**
- Deploy solution : SLOT_1
- View cluster and external IP addressing : SLOT_2
- Implement a single, public IP endpoint that is routed to multiple microservices.: SLOT_3


> **1. Deploy solution : Helm**  
> Helm helps you manage Kubernetes applications — Helm Charts help you define, install, and upgrade even the most complex Kubernetes application. To create the ingress controller, use Helm to install nginx-ingress.  
>
> **2. View cluster and external IP addressing : Kubectl**  
> The Kubernetes command-line tool, kubectl, allows you to run commands against Kubernetes clusters. To find the cluster IP address of a Kubernetes pod, use the kubectl get pod command on your local machine, with the option -o wide .
>
> **3. Implement a single, public IP endpoint that is routed to multiple microservices.: Ingress Controller**  
> An ingress controller is a piece of software that provides reverse proxy, configurable traffic routing, and TLS termination for Kubernetes services. Kubernetes ingress resources are used to configure the ingress rules and routes for individual Kubernetes services. Using an ingress controller and ingress rules, a single IP address can be used to route traffic to multiple services in a Kubernetes cluster.

- https://chatgpt.com/share/6742e26a-8560-8000-a66b-b77972318443

---

### Q113
**You are implementing an order processing system. A point of sale application publishes orders to topics in an Azure Service Bus queue. The Label property for the topic includes the following data:**  
| Property | Description |  
| --- | --- |
| ShipLocation | the country/region where the order will be shipped |
| CorrelationId | a priority value for the order | 
| Quantity | a user-defined field that stores the quantity of items in an order |
| AuditedAt | a user-defined field that records the date an order is audited |

**The system has the following requirements for subscriptions:**
| subscription | Comments | 
| --- | --- |
| FutureOrders | This subscription is reserved for future use and must not receive any orders |
| HighPriorityOrders | Handle all high priority orders and international orders |
| InternationalOrders | Handle orders where the country/region is not United States |
| HighQuantityOrders | Handle orders with quantities greater than 100 units |
| AllOrders | This subscription is used for auditing purposes. This subscription must receive every single order. AllOrders has an Action defined that updates the `AuditedAt` property to include the date and time it was received by the subscription. |

**You need to implement ltering and maximize throughput while evaluating lters. Which lter types should you implement?**

- FutureOrders
    - [SqlFilter](#q113)
    - CorrelationFilter
    - NoFilter
> **`SqlFilter`** with a condition that will never be true (e.g., `1 = 0`). This ensures no messages are received.

- HighPriorityOrders
    - SqlFilter
    - [CorrelationFilter](#q113)
    - NoFilter
> **`CorrelationFilter`** holds a set of conditions that are matched against one or more of an arriving message's user and system properties. A common use is to match against the `CorrelationId` property,

- InternationalOrders
    - [SqlFilter](#q113)
    - CorrelationFilter
    - NoFilter
> **`SqlFilter`** to evaluate the `ShipLocation` field.  
> `ShipLocation <> 'United States'`

- HighQuantityOrders
    - [SqlFilter](#q113)
    - CorrelationFilter
    - NoFilter
> **`SqlFilter`** to evaluate the `Quantity` field.  
> `Quantity > 100`

- AllOrders
    - SqlFilter
    - CorrelationFilter
    - [NoFilter](#q113)
> No filtering is needed because this subscription is supposed to receive all orders.

- https://learn.microsoft.com/en-us/azure/service-bus-messaging/topic-filters#filters

---

### Q114
**Your company has several websites that use a company logo image. You use Azure Content Delivery Network (CDN) to store the static image.  
You need to determine the correct process of how the CDN and the Point of Presence (POP) server will distribute the image and list the items in the correct order.  
In which order do the actions occur?**

- If no edge servers in the POP have the image in cache, the POP requests the file from the origin server.
- A user requests the image from the CDN URL. The DNS routes the request to the best performing POP location.
- Subsequent requests for the file may be directed to the same POP using the CDN logo image URL. The POP edge server returns the file from cache if the TTL has not expired.
- The origin server returns the logo image to an edge server in the POP. An edge server in the POP caches the logo image and returns the image to the client.

> **1. A user requests the image from the CDN URL. The DNS routes the request to the best performing POP location.**  
> This is the first step where the client makes a request, and the CDN uses DNS to determine the optimal POP based on factors like latency and geography.
>
> **2. If no edge servers in the POP have the image in cache, the POP requests the file from the origin server.**  
> If the requested image is not cached on the POP edge servers, they forward the request to the origin server where the file is stored.
>
> **3. The origin server returns the logo image to an edge server in the POP. An edge server in the POP caches the logo image and returns the image to the client.**  
> The origin server fulfills the request by sending the image to the edge server in the POP, which caches it and serves it to the user.  
>
> **4. Subsequent requests for the file may be directed to the same POP using the CDN logo image URL. The POP edge server returns the file from cache if the TTL has not expired.**  
> For subsequent requests, if the Time-to-Live (TTL) of the cached image hasn't expired, the POP edge server serves the image directly from its cache, improving performance and reducing load on the origin server.

- https://chatgpt.com/share/67433b8a-d18c-8000-a805-a47d6a1fa47f

---

### Q115
**You are developing an Azure Cosmos DB solution by using the Azure Cosmos DB SQL API. The data includes millions of documents. Each document may contain hundreds of properties.  
The properties of the documents do not contain distinct values for partitioning. Azure Cosmos DB must scale individual containers in the database to meet the performance needs of the application by spreading the workload evenly across all partitions over time.  
You need to select a partition key. Which two partition keys can you use?**

- a single property value that does not appear frequently in the documents
- a value containing the collection name
- a single property value that appears frequently in the documents
- [a concatenation of multiple property values with a random sux appended](#q115)
- [a hash suffix appended to a property value](#q115)

> **A single property value that does not appear frequently in the documents**  
**Not recommended:** If the property value does not appear frequently, it could result in "hot partitions," where only one or a few partitions handle most of the requests. This creates an uneven workload and reduces scalability.
>
> **A value containing the collection name**  
**Not recommended:** Using the collection name as a partition key can cause all data to be routed to a single partition, defeating the purpose of partitioning.
>
> **A single property value that appears frequently in the documents**  
**Not recommended:** If a single property value appears frequently (e.g., all documents have the same value), all the data will be stored in one partition, leading to a hot partition.
>
> **A concatenation of multiple property values with a random suffix appended**  
**Recommended:** Combining multiple property values with a random suffix ensures that the partition key values are distributed more evenly, reducing the risk of hot partitions. This approach spreads the workload across multiple partitions effectively.
>
> **A hash suffix appended to a property value**  
**Recommended:** Appending a hash suffix to a property value is another effective way to achieve even distribution of data across partitions. It ensures that the workload is spread out evenly and avoids hot partitions.

- https://chatgpt.com/share/6743545b-12c0-8000-b07b-be1b06540193
- https://learn.microsoft.com/en-us/azure/cosmos-db/nosql/synthetic-partition-keys

---

### Q116
**You are developing an Azure-hosted e-commerce web application. The application will use Azure Cosmos DB to store sales orders.  
You are using the latest SDK to manage the sales orders in the database. You create a new Azure Cosmos DB instance.   
You include a valid endpoint and valid authorization key to an appSettings.json file in the code
project.  
You are evaluating the following application code:
```csharp
using System;
using System. Threading.Tasks;
using Microsoft.Azure.Cosmos;
using Microsoft.Extensions.Configuration;
using Newtonsoft.Json;
namespace SalesOrders {
    public class SalesOrder { }

    internal class ManageSalesOrders {
        private static async Task GenerateSalesOrders (){
            ConfigurationRoot configuration = new ConfigurationBuilder().AddJsonFile ("appsettings.json").Build();
            string endpoint = configuration ["EndPointUrl"];
            string authKey = configuration ["AuthorizationKey"];
            using CosmosClient client = new CosmosClient (endpoint, authKey) ;
            Database database = null;
            using (await client.GetDatabase("SalesOrders").DeleteStreamAsync ()) {} 
            database = await client.CreateDatabaseIfNotExistsAsync("SalesOrders") ;
            Container container1 = await database.CreateContainerAsync(id: "Container1", partitionKeyPath: "/AccountNumber");
            Container container2 = await database.CreateContainerAsync(id: "Container2", partitionKeyPath: "/AccountNumber");
            SalesOrder salesOrder1 = new SalesOrder () { AccountNumber = "123456" };
            await container1.CreateItemAsync(salesOrder1, new PartitionKey (salesOrder1.AccountNumber));
            SalesOrder salesOrder2 = new SalesOrder () { AccountNumber = "654321" };
            await container1.CreateItemAsync(salesOrder2, new PartitionKey (salesOrder2.AccountNumber));
            SalesOrder salesOrder3 = new SalesOrder () { AccountNumber = "109876" };
            await container2.CreateItemAsync(salesOrder3, new PartitionKey (salesOrder3.AccountNumber)) ;
            _ = await database.CreateUserAsync ("User1") ;
            User user1 = database.GetUser("'User1") ;
            _ = await user1.ReadAsync () ;
        }
    }
}   
```
**For each of the following statements, select Yes if the statement is true. Otherwise, select No.**

- A database named SalesOrders is created. The database will include two containers.
    - [Yes](#q116)
    - No

- Container 1 will contain two items.
    - [Yes](#q116)
    - No

- Container2 will contain one item.
    - [Yes](#q116)
    - No

> **A database named SalesOrders is created. The database will include two containers.**   
**Yes:** The database is created (or reused), and two containers (`container1` and `container2`) are added.
>
> **Container1 will contain two items.**   
**Yes:** Two items (`salesOrder1` and `salesOrder2`) are added to `container1`.
>
> **Container2 will contain one item.**   
**Yes:** One item (`salesOrder3`) is added to `container2`.

- https://chatgpt.com/share/67436d05-8f9c-8000-b47f-d47afa1c15f1

---

### Q117
**You develop an Azure solution that uses Cosmos DB.  
The current Cosmos DB container must be replicated and must use a partition key that is optimized for queries.  
You need to implement a change feed processor solution.  
Which change feed processor components should you use? To answer, drag the appropriate components to the correct requirements.**

**Components:**
- Host
- Delegate
- Lease container
- Monitored container

**Requirements:**
- Store the data from which the change feed is generated. : SLOT_1
- Coordinate processing of the change feed across multiple workers. :  SLOT_2
- Use the change feed processor to listen for changes. : SLOT_3
- Handle each batch of changes. : SLOT_4

> Store the data from which the change feed is generated: **Monitored container**  
The monitored container is the container in Cosmos DB where the data is stored and from which changes are captured in the change feed.
>
> Coordinate processing of the change feed across multiple workers: **Lease container**  
The lease container stores the leases used by the change feed processor to distribute and coordinate processing across multiple worker instances.
>
> Use the change feed processor to listen for changes: **Host**   
The host is responsible for running the change feed processor and listening for changes in the monitored container.
>
>Handle each batch of changes: **Delegate**  
The delegate is the user-provided code (a delegate or callback) that processes each batch of changes delivered by the change feed.

- https://chatgpt.com/share/67437055-d764-8000-b69d-62263d212ca4

---

### Q118

**You are developing a web application that will use Azure Storage. Older data will be less frequently used than more recent data.  
You need to congure data storage for the application. You have the following requirements:  
• Retain copies of data for five years.  
• Minimize costs associated with storing data that is over one year old.  
• Implement Zone Redundant Storage for application data.  
What should you do?**

**Requirements:**
- Configure an Azure Storage account
    - Implement Blob Storage
    - Implement Azure Cosmos DB
    - Implement Storage (general purpose v1)
    - [Implement StorageV2 (general purpose v2)](#q118)

Configure data retention
    - Snapshot blobs and move them to the archive tier
    - [Set a lifecycle management policy to move blobs to the cool tier](#q118)
    - Use AzCopy to copy the data to an on-premises device for backup
    - Set a lifecycle management policy to move blobs to the archive tier

> Only storage accounts that are configured for LRS, GRS, or RA-GRS support moving blobs to the archive tier. The archive tier isn't supported for ZRS, GZRS, or RA-GZRS accounts.

- https://learn.microsoft.com/en-us/azure/storage/blobs/access-tiers-overview#archive-access-tier

---

### Q119
**A company develops a series of mobile games. All games use a single leaderboard service. You have the following requirements:  
• Code must be scalable and allow for growth.  
• Each record must consist of a playerId, gameId, score, and time played.  
• When users reach a new high score, the system will save the new score using the SaveScore function below.  
Each game is assigned an Id based on the series title. You plan to store customer information in Azure Cosmos DB.  
The following data already exists in the database:
| PartitionKey | RowKey | Email |
|--------------|--------|-------|
| Harp | Smith | wharp@contoso.com |
| Smith | Smith | ssmith@contoso.com |
| Smith | Jeff | jsmith@contoso.com |

**You develop the following code to save scores in the data store.**
```csharp
public void SaveScore (string gameId, string playerId, int score, long timePlayed){
    CloudStorageAccount storageAccount = CloudStorageAccount.Parse(connectionString);
    CloudTableClient tableClient = storageAccount.CreateCloudTableClient();
    CloudTable table = tableClient.GetTableReference("scoreTable");
    table.CreateIfNotExists();
    var scoreRecord = new PlayerScore(gameld, playerId, score, timePlayed);
    TableOperation insertOperation = TableOperation.Insert(scoreRecord);
    table.Execute(insertOperation);
}
```

**You develop the following code to query the database**
```csharp
    CloudTableClient tableClient = account.CreateCloudTableClient();
    CloudTable table = tableClient.GetTableReference("people");
    TableQuery <CustomerEntity> query = new TableQuery <CustomerEntity>()
    .Where(TableQuery.CombineFilters(
        TableQuery.GenerateFilterCondition(PartitionKey, QueryComparisons.Equal, "Smith") ,
        TableOperators.And, 
        TableQuery.GenerateFilterCondition(Email,Querycomparisons.Equal "ssmith@contoso.com")));
    await table.ExecuteQuerySegmentedAsync<CustonerEntity>(query, null);
```

**For each of the following statements, select Yes if the statement is true. Otherwise, select No**

- SaveScore will work with Cosmos DB.
    - Yes
    - [No](#q119)  
> The `SaveScore` method uses Azure Table Storage APIs (`CloudStorageAccount`, `CloudTableClient`, `CloudTable`) to interact with a table named scoreTable. Azure Cosmos DB supports a Table API mode, but this method is written explicitly for Azure Table Storage, not Cosmos DB.
- https://learn.microsoft.com/en-us/azure/cosmos-db/table/quickstart-dotnet

- SaveScore will update and replace a record if one already exists with the same playerId and gameId.
    - Yes
    - [No](#q119)
> The method uses `TableOperation.Insert(scoreRecord)`, which attempts to insert a new record. This will fail with an error if a record with the same `PartitionKey` and `RowKey` already exists. To replace or update a record, `TableOperation.InsertOrReplace` should be used instead.

- Leader board data for the game will be automatically partitioned using gameId.
    - Yes
    - [No](#q119) 
> The partitioning of Azure Table Storage (or Cosmos DB using the Table API) is determined by the `PartitionKey` in the table schema. The `PartitionKey` is not explicitly set in the `SaveScore` method. Instead, it depends on the implementation of the `PlayerScore` class, which is not shown. Without explicitly setting `gameId` as the `PartitionKey`, there is no guarantee that data will be partitioned by `gameId`.

- SaveScore will store the values for the gameId and playerId parameters in the database.
    - [Yes](#q119)
    - No
> The `SaveScore` method creates a new instance of the `PlayerScore` class and passes `gameId` and `playerId` as parameters. Assuming the `PlayerScore` class correctly maps these parameters to table properties, these values will be stored in the database.

- https://chatgpt.com/share/674377a6-0b9c-8000-90f0-b2961d283550

---

### Q120
**You develop and deploy a web application to Azure App Service. The application accesses data stored in an Azure Storage account.  
The account contains several containers with several blobs with large amounts of data. You deploy all Azure resources to a single region.  
You need to move the Azure Storage account to the new region. You must copy all data to the new region.  
What should you do first?**

- [Export the Azure Storage account Azure Resource Manager template](#q120)
- Initiate a storage account failover
- Congure object replication for all blobs
- Use the AzCopy command line tool
- Create a new Azure Storage account in the current region
- Create a new subscription in the current region

> To move a storage account, create a copy of your storage account in another region. Then, move your data to that account by using AzCopy, or another tool of your choice and nally, delete the resources in the source region.  
> To get started, export, and then modify a Resource Manager template.

- https://chatgpt.com/share/6743785b-19f0-8000-91cd-9aea03c27bc7
- https://learn.microsoft.com/en-us/azure/operational-excellence/relocation-storage-account?tabs=azure-portal

---

### Q121
**You are developing an application to collect the following telemetry data for delivery drivers:  
first name, last name, package count, item id, and current location coordinates.   
The app will store the data in Azure Cosmos DB. You need to congure Azure Cosmos DB to query the data.  
Which values should you use?**

- Azure Cosmos DB API
    - Gremlin
    - Table API
    - [Core SQL](#q121)

- Partition Key
    - first name
    - last name
    - package count
    - [item id](#q121)

> **Core SQL:** Best for querying structured or semi-structured data (JSON). It supports SQL-like queries, making it ideal for handling and querying data like first name, last name, package count, item id, and current location coordinates.
>
> **Item ID:** This is likely to be a unique and stable identifier (e.g., for packages). Using item id as the partition key ensures even data distribution and efficient querying.

- https://chatgpt.com/share/6743f80d-5064-8000-95bb-1ffdbe88e866
- https://learn.microsoft.com/en-us/azure/cosmos-db/choose-api
- https://learn.microsoft.com/en-us/azure/cosmos-db/partitioning-overview

---

### Q122
**You are implementing an Azure solution that uses Azure Cosmos DB and the latest Azure Cosmos DB SDK. You add a change feed processor to a new container instance.  
You attempt to read a batch of 100 documents. The process fails when reading one of the documents.  
The solution must monitor the progress of the change feed processor instance on the new container as the change feed is read.   
You must prevent the change feed processor from retrying the entire batch when one document cannot be read.  
You need to implement the change feed processor to read the documents.  
Which features should you use?**

**Features:**
- Change feed estimator
- Requirement
- Dead-letter queue
- Deployment unit
- Lease container

**Requirements:**  
- Monitor the progress of the change feed processor : SLOT_1  
- Prevent the change feed processor from retrying the entire batch when one document cannot be read : SLOT_2  

> SLOT_1: **Change feed estimator**  
> You can use the change feed estimator to monitor the progress of your change feed processor instances as they read the change feed or use the life cycle notications to detect underlying failures.
>
> SLOT_2: **Dead-letter queue**   
> To prevent your change feed processor from getting "stuck" continuously retrying the same batch of changes, you should add logic in your delegate code to write documents, upon exception, to a dead-letter queue. This design ensures that you can keep track of unprocessed changes while still being able to continue to process future changes. The dead-letter queue might be another Cosmos container. The exact data store does not matter, simply that the unprocessed changes are persisted.

- https://chatgpt.com/share/6743fa9a-6730-8000-b728-f3a5099556fb
- https://learn.microsoft.com/en-us/azure/cosmos-db/nosql/change-feed-processor?tabs=dotnet#error-handling
- https://learn.microsoft.com/en-us/azure/cosmos-db/nosql/how-to-use-change-feed-estimator?tabs=dotnet

---

### Q123
**You are developing an application that uses a premium block blob storage account. The application will process a large volume of transactions daily. You enable Blob storage versioning.  
You are optimizing costs by automating Azure Blob Storage access tiers. You apply the following policy rules to the storage account.**
```json
{
    "rules":[
        {
            "name": "versionRule",
            "enabled": true,
            "type": "Lifecycle",
            "definition": {
                "actions": {
                    "version": {
                        "tierToCool": {
                            "daysAfterCreationGreaterThan": 60
                        },
                        "delete": {
                            "daysAfterCreationGreaterThan": 365
                        }
                    }
                },
                "filters": {
                    "blobTypes": ["blockBlob"],
                    "prefixMatch": ["transactions"]
                }
            }
        }
    ]
}
```
**For each of the following statements, select Yes if the statement is true. Otherwise, select No.**

- Block blobs prefixed with transactions will transition blobs that have not been modified in over 60 days to cool storage, and delete blobs not modified in 365 days.
    - Yes
    - [No](#q123)
> The `tierToCool` action applies to previous versions of block blobs after 60 days of creation, not based on modification. Similarly, deletion occurs after 365 days of creation, not modification. Would be true if `daysAfterModificationGreaterThan` was used.

- Blobs are moved to cool storage if they have not been accessed for 60 days.
    - Yes
    - [No](#q123)
> The policy moves versions of block blobs to the cool tier 60 days after their creation, regardless of access or modification status. Azure Blob Storage lifecycle policies do not evaluate blob access times. Would be true if `daysAfterLastAccessGreaterThan` was used.

- The policy rule tiers previous versions within a container named transactions that are 60 days or older to the cool tier and deletes previous versions that are 365 days or older.
    - [Yes](#q123)
    - No
> The lifecycle policy targets versions of block blobs that match the prefix `transactions`. It transitions these versions to the cool tier after 60 days and deletes them after 365 days, as specified in the policy.

- Blobs will automatically be tiered from cool back to hot if accessed again after
being tiered to cool.
    - Yes
    - [No](#q123)
> `"enableAutoTierToHotFromCool": "true"` should be enabled. Also this option is not supported for snapshots & versions.


- https://learn.microsoft.com/en-us/azure/storage/blobs/lifecycle-management-overview
- https://learn.microsoft.com/en-us/azure/storage/blobs/lifecycle-management-overview#rule-actions

---

### Q124
**An organization deploys Azure Cosmos DB.  
You need to ensure that the index is updated as items are created, updated, or deleted.  
What should you do?**

- Set the indexing mode to Lazy.
- Set the value of the automatic property of the indexing policy to False.
- Set the value of the EnableScanInQuery option to True.
- [Set the indexing mode to Consistent.] (#q124)

> Azure Cosmos DB provides three indexing modes:   
> **1. Consistent:** Ensures that the index is updated synchronously with create, update, or delete operations. This mode guarantees that queries will always return the most up-to-date data.  
> **2. Lazy:** Index updates are performed asynchronously, which can result in stale index data during queries but may improve write performance.  
> **3. None:** Indexing is disabled on the container. This mode is commonly used when a container is used as a pure key-value store without the need for secondary indexes. It can also be used to improve the performance of bulk operations.
>
> **Set the indexing mode to Lazy:** This would delay index updates and not meet the requirement for real-time index consistency.   
> **Set the value of the automatic property of the indexing policy to False:** This disables automatic indexing, which would require you to manually manage indexes. This does not ensure real-time updates.  
> **Set the value of the EnableScanInQuery option to True:** This option allows queries to scan the full database for results instead of using the index. It does not affect index updating behavior.  

- https://chatgpt.com/share/6744214f-7b5c-8000-af59-2c5b58f66f3e
- https://learn.microsoft.com/en-us/azure/cosmos-db/index-policy

---

### Q125
**You are developing a .Net web application that stores data in Azure Cosmos DB. The application must use the Core API and allow millions of reads and writes.  
The Azure Cosmos DB account has been created with multiple write regions enabled. The application has been deployed to the East US2 and Central US regions.  
You need to update the application to support multi-region writes.  
What are two possible ways to achieve this goal?**

- [Update the ConnectionPolicy class for the Cosmos client and populate the PreferredLocations property based on the geo-proximity of the application.](#q125)
- Update Azure Cosmos DB to use the Strong consistency level. Add indexed properties to the container to indicate region.
- [Update the ConnectionPolicy class for the Cosmos client and set the UseMultipleWriteLocations property to true.](#q125)
- Create and deploy a custom conict resolution policy.
- Update Azure Cosmos DB to use the Session consistency level. Send the SessionToken property value from the FeedResponse object of the write action to the end-user by using a cookie.

> **"You need to update the application to support multi-region writes"**  
> i.e., is enable multi-region writes (bool, option C) and add the regions (option A)  
> Then you have to apply the Conflict resolution policies.This can be LLW(default, not mentioned) or custom (option D).   
> Hence, there is only ONE way to to support multi-region writes (both apply C AND A) and there are subsequently TWO ways to apply the Conflict resolution policies to solve write, update and delete conflicts of which one is mentioned in the question (D).  
> To support multi-region writes answer would be A and C, but they have to be set both, not one or the other.

- https://chatgpt.com/share/67443f52-4654-8000-8492-f6df8a44a7c3
- https://learn.microsoft.com/en-us/azure/cosmos-db/nosql/how-to-multi-master?tabs=api-async
- https://learn.microsoft.com/en-us/azure/cosmos-db/conflict-resolution-policies

---

### Q126
**You are developing a solution to store documents in Azure Blob storage. Customers upload documents to multiple containers. Documents consist of PDF, CSV, Microsoft Office format and plain text files.  
The solution must process millions of documents across hundreds of containers. The solution must meet the following requirements:  
• Documents must be categorized by a customer identier as they are uploaded to the storage account.  
• Allow ltering by the customer identier.  
• Allow searching of information contained within a document.  
• Minimize costs.  
You create and congure a standard general-purpose v2 storage account to support the solution.  
You need to implement the solution. What should you implement?**

**Requirement:**

- Search and filter by customer identifier
    - Azure Cognitive Search
    - [Azure Blob index tags](#q126)
    - Azure Blob inventory policy
    - Azure Blob metadata
> Blob index tags allow you to assign key-value pairs to blobs, making them easily filterable using the Azure Blob storage service. This is an efficient and cost-effective option for filtering blobs without additional infrastructure.

- Search information inside documents
    - [Azure Cognitive Search](#q126)
    - Azure Blob index tags
    - Azure Blob inventory policy
    - Azure Blob metadata
> Azure AI Search (formerly known as "Azure Cognitive Search") can extract and index text from various document types (e.g., PDF, Microsoft Office files, plain text) and provide powerful full-text search capabilities.

- https://chatgpt.com/share/674446a3-0ed8-8000-82d5-a77cfe7b3fc8
- https://learn.microsoft.com/en-us/azure/storage/blobs/storage-manage-find-blobs?tabs=azure-portal
- https://learn.microsoft.com/en-us/azure/search/search-blob-storage-integration

---

### Q127
**You are developing a web application by using the Azure SDK. The web application accesses data in a zone-redundant BlockBlobStorage storage account.  
The application must determine whether the data has changed since the application last read the data. Update operations must use the latest data changes when writing data to the storage account.  
You need to implement the update operations.  
Which values should you use?**

- HTTP Header value
    - [ETag](#q127)
    - Last Modified
    - VersionId

- Conditional header
    - [If-Match](#q127)
    - If-Modified-Since
    - If-None-Match

> **ETag (Entity Tag)** is a unique identifier assigned by Azure Blob Storage to the blob's version or state. Every time a blob is modified, its ETag changes. You can use ETags to check if the blob has been modified since the last time your application accessed it.  
>
> The **`If-Match`** conditional header ensures that an update operation (e.g., PUT or DELETE) is performed only if the ETag of the blob matches the value provided in the request. This approach prevents overwriting a blob if it has been updated by another process since the application last read it.
>
> **`Last Modified:`**  
Represents the timestamp when the blob was last modified. It's less precise than ETag because it doesn't provide a way to uniquely identify changes and is susceptible to clock skew issues.  
>
> **`VersionId:`**  
Used in accounts with versioning enabled to identify specific versions of blobs. While useful in versioning scenarios, it's not needed for detecting changes in a zone-redundant BlockBlobStorage account where versioning isn't explicitly mentioned.  
>
> **`If-Modified-Since:`**  
A DateTime value. Specify this header to perform the operation only if the resource has been modified since the specified time.  
>
> **`If-None-Match:`**  
Performs an action only if the blob's ETag does **not** match the provided value.
This is typically used for GET operations (e.g., to retrieve data only if it has changed) rather than update operations.

- https://learn.microsoft.com/en-us/azure/storage/blobs/concurrency-manage#optimistic-concurrency
- https://learn.microsoft.com/en-us/rest/api/storageservices/specifying-conditional-headers-for-blob-service-operations

---

### Q128
**An organization deploys a blob storage account. Users take multiple snapshots of the blob storage account over time.  
You need to delete all snapshots of the blob storage account. You must not delete the blob storage account itself.  
How should you complete the code segment?**
```
Azure.Storage.Blobs.Models.DeleteSnapshotsOption snapshotsOption = Azure.Storage.Blobs.Models.SLOT_1.SLOT_2;
```
- SLOT_1
    - DeleteIfExists
    - [DeleteSnapshotsOption](#q128)
    - WithSnapshot
    - WithSnapshotCore

- SLOT_2
    - IncludeSnapshots
    - None
    - [OnlySnapshots](#q128)

```csharp
public static async Task DeleteBlobSnapshotsAsync(BlobClient blob) {
    // Delete a blob and all of its snapshots
    await blob.DeleteAsync(snapshotsOption: DeleteSnapshotsOption.IncludeSnapshots);

    // Delete only the blob's snapshots
    await blob.DeleteAsync(snapshotsOption: DeleteSnapshotsOption.OnlySnapshots);
}
```

- https://learn.microsoft.com/en-us/dotnet/api/azure.storage.blobs.models.deletesnapshotsoption?view=azure-dotnet
- https://learn.microsoft.com/en-us/azure/storage/blobs/storage-blob-delete#delete-a-blob

---

### Q129
**You are developing an application that monitors data added to an Azure Blob storage account.  
You need to process each change made to the storage account.  
How should you complete the code segment?**
```
var changeFeedClient = new BlobServiceClient("...").GetChangeFeedClient();
var x = default(string);
while (true){
    var changeFeed = changeFeedClient.SLOT_1;
    foreach (var c in changeFeed){
        x = c.SLOT_2;
        ProcessChanges(c.Values);
    }
}
```

- SLOT_1
    - GetChanges()
    - GetChangesAsync()
    - [GetChanges(x).AsPages()](#q129)
    - GetChanges(x).GetEnumerator()

- SLOT_2
    - [ContinuationToken](#q129)
    - GetRawResponse().ReasonPhrase
    - Values.Max(x => x.EventTime).ToString()
    - Values.Min(x => x.EventTime).ToString()

> `changeFeedClient.GetChanges(x).AsPages()` returns an `IEnumerable<Page<BlobChangeFeedEvent>>`  when you loop through these pages (i.e.,`Page<BlobChangeFeedEvent>`) you will get the options `page.ContinuationToken` and `page.Values` which are used in this example.
```csharp
var changeFeedClient = new BlobServiceClient("...").GetChangeFeedClient();
var x = default(string);
while (true) {
    var changeFeed = changeFeedClient.GetChanges(x).AsPages();
    foreach (var c in changeFeed) {
        x = c.ContinuationToken;
        ProcessChanges(c.Values);
    }
}
```

- https://chatgpt.com/share/6744c24d-6d20-8000-8f3d-ba4c81547b36
- https://github.com/Azure/azure-sdk-for-net/tree/main/sdk/storage/Azure.Storage.Blobs.ChangeFeed#resume-with-continuationtoken

---

### Q130
**You develop an application that sells AI generated images based on user input. You recently started a marketing campaign that displays unique ads every second day.  
Sales data is stored in Azure Cosmos DB with the date of each sale being stored in a property named `whenFinished`.  
The marketing department requires a view that shows the number of sales for each unique ad.   
You need to implement the query for the view.  
How should you complete the query?** 

```
select SLOT_1, SLOT_2
from c
group by SLOT_3
```

- SLOT_1
    - max(c.whenFinished)
    - sum(c.whenFinished)
    - count(c.whenFinished)

- SLOT_2
    - DateTimeBin(c.whenFinished, "day", 2)
    - DateTimePart(c.whenFinished, "day", 2)
    - DateTimeBin(c.whenFinished, "hour", 12)
    - DateTimePart(c.whenFinished, "hour", 12)

- SLOT_3
    - DateTimeBin(c.whenFinished, "day", 2)
    - DateTimePart(c.whenFinished, "day", 2)
    - DateTimeBin(c.whenFinished, "hour", 12)
    - DateTimePart(c.whenFinished, "hour", 12)

> **SLOT_1: The required aggregation**  
The marketing department needs the number of sales for each unique ad. Therefore, you should use `count(c.whenFinished)` in SLOT_1 to count the number of sales.
>
> **SLOT_2: Binning sales into 2-day intervals**  
The marketing campaign runs with ads changing every second day, so you need to group sales into 2-day bins. The function `DateTimeBin(c.whenFinished, "day", 2)` bins dates into 2-day intervals and fits the requirement.
>
> **SLOT_3: Grouping criteria**
Since you are grouping by 2-day intervals, SLOT_3 also needs to use `DateTimeBin(c.whenFinished, "day", 2)` to ensure grouping aligns with the 2-day binning logic.
>
> **DateTimeBin:** Groups or "bins" datetime values into fixed-sized intervals. It's typically used for creating time-based aggregations over a specified period (e.g., grouping data into daily, hourly, or custom time intervals).   
> syntax: `DateTimeBin(datetime_field, granularity, size)`
>
> **DateTimePart:** Extracts a specific part of a datetime value (e.g., year, month, day, hour) for analysis or filtering. It does not group values but rather focuses on identifying a specific portion of the date or time.  
> syntax: `DateTimePart(datetime_field, part)`


- https://chatgpt.com/share/6744c772-07ac-8000-888b-39fcd40494dc
- https://learn.microsoft.com/en-us/azure/cosmos-db/nosql/query/system-functions
- https://learn.microsoft.com/en-us/azure/cosmos-db/nosql/query/datetimepart
- https://learn.microsoft.com/en-us/azure/cosmos-db/nosql/query/datetimebin

---

### Q131
**You implement an Azure solution to include Azure Cosmos DB, the latest Azure Cosmos DB SDK, and the Core (SQL) API.  
You also implement a change feed processor on a new container instance by using the Azure Functions trigger for Azure Cosmos DB.  
A large batch of documents continues to fail when reading one of the documents in the batch. The same batch of documents is continuously retried by the triggered function and a new batch of documents must be read.   
You need to implement the change feed processor to read the documents.  
Which feature should you implement?**

**Features:**
- Lease container
- Dead-letter queue
- Life-cycle notifications
- Change feed estimator  

**Requirements:**
- Read a new batch of documents while keeping track of the failing batch of documents. : SLOT_1
- Handle errors in the change feed processor. : SLOT_2

> SLOT_1: **Dead-letter queue**  
> Dead-letter queues are designed to store problematic documents that fail processing, allowing the system to move on and process new documents without being stuck retrying the failing ones.
>
> SLOT_2: **Life-cycle notifications**  
> Life-cycle notifications allow for handling custom events, such as logging errors or implementing retry logic, when processing documents in the change feed processor. Register a handler for `WithErrorNotification` to be notified when the current host encounters an exception during processing.

```csharp
Container.ChangeFeedMonitorErrorDelegate onErrorAsync = (string LeaseToken, Exception exception) =>
{
    if (exception is ChangeFeedProcessorUserException userException)
    {
        Console.WriteLine($"Lease {LeaseToken} processing failed with unhandled exception from user delegate {userException.InnerException}");
    }
    else
    {
        Console.WriteLine($"Lease {LeaseToken} failed with {exception}");
    }

    return Task.CompletedTask;
};

ChangeFeedProcessor changeFeedProcessor = monitoredContainer
    .GetChangeFeedProcessorBuilder<ToDoItem>("changeFeedNotifications", handleChanges)
    .WithErrorNotification(onErrorAsync)
    .WithInstanceName("consoleHost")
    .WithLeaseContainer(leaseContainer)
    .Build();
```

- https://chatgpt.com/share/6745a756-54e8-8000-94fb-7c69a6b5f60f
- https://learn.microsoft.com/en-us/azure/cosmos-db/nosql/change-feed-processor?tabs=dotnet#error-handling
- https://learn.microsoft.com/en-us/azure/cosmos-db/nosql/change-feed-processor?tabs=dotnet#life-cycle-notifications

---

### Q132
**You are developing an application to store business-critical data in Azure Blob storage.  
The application must meet the following requirements:  
• Data must not be modied or deleted for a user-specied interval.  
• Data must be protected from overwrites and deletes.  
• Data must be written once and allowed to be read many times.  
You need to protect the data in the Azure Blob storage account.  
Which two actions should you perform?**

- [Congure a time-based retention policy for the storage account.](#q132)
- Create an account shared-access signature (SAS).
- Enable the blob change feed for the storage account.
- [Enable version-level immutability support for the storage account.](#q132)
- Enable point-in-time restore for containers in the storage account.
- Create a service shared-access signature (SAS)

> A time-based retention policy stores blob data in a Write-Once, Read-Many (WORM) format for a specified interval. When a time-based retentio policy is set, clients can create and read blobs, but can't modify or delete them. After the retention interval has expired, blobs can be deleted but
not overwritten.  
> Before you can apply a time-based retention policy to a blob version, you must enable support for version-level immutability.

- https://chatgpt.com/share/6745b85a-58ec-8000-b734-6b8de9cad61b
- https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-storage-overview#time-based-retention-policies
- https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-policy-configure-version-scope?tabs=azure-portal

---

### Q133
**You are updating an application that stores data on Azure and uses Azure Cosmos DB for storage. The application stores data in multiple documents associated with a single username.  
The application requires the ability to update multiple documents for a username in a single ACID operation.  
You need to congure Azure Cosmos DB.  
Which two actions should you perform?**

- Create a collection sharded on username to store documents.
- Congure Azure Cosmos DB to use the Gremlin API.
- [Create an unsharded collection to store documents.](#q133)
- [Congure Azure Cosmos DB to use the MongoDB API.](#q133)

> The MongoDB API supports multi-document ACID transactions, which allow you to update multiple documents in a single atomic operation.  
> Multi-document transactions are not supported across collections or in sharded collections in 4.0.

- https://learn.microsoft.com/en-us/azure/cosmos-db/mongodb/use-multi-document-transactions#requirements

---

### Q134
You develop Azure solutions. You must connect to a No-SQL globally-distributed database by using the .NET API.  
You need to create an object to congure and execute requests in the database. Which code segment should you use?  
``` 
database_name = 'MyDatabase' 
database = client.create_database_if_not_exists(id=database_name)
```
```
client = new CosmosClient(endpoint, key)
```
```
container_name = 'MyContainer'
container = database.create_container_if_not_exists(
    id=container_name, 
    partition_key=PartitionKey(path="/lastName"), 
    offer_throughput=400 
)
```

> **`client = new CosmosClient(endpoint, key)`** is the correct option for initializing a `CosmosClient` object in .NET, which is required to configure and execute requests in Azure Cosmos DB.

- https://learn.microsoft.com/en-us/dotnet/api/microsoft.azure.cosmos.cosmosclient?view=azure-dotnet#examples

---

### Q135
**You develop a web application that provides access to legal documents that are stored on Azure Blob Storage with version-level immutability policies.  
Documents are protected with both time-based policies and legal hold policies. All time-based retention policies have the `AllowProtectedAppendWrites` property enabled.  
You have a requirement to prevent the user from attempting to perform operations that would fail only when a legal hold is in effect and when all other policies are expired.  
You need to meet the requirement.  
Which two operations should you prevent?**

- adding data to documents
- [deleting documents](#q135)
- creating documents
- [overwriting existing documents](#q135)

> **Adding data to documents:**  
> The `AllowProtectedAppendWrites` property allows appending data to append blobs even if a time-based retention policy is active. However, appending is not impacted by a legal hold; this operation would succeed. Preventing this operation is unnecessary.
>
> **Deleting documents:**  
> Documents cannot be deleted when a legal hold is in effect, even if the time-based retention policies are expired. Deletion would fail under the described condition. This operation should be prevented.
>
> **Creating documents:**  
> Creating new blobs (documents) is not restricted by a legal hold or time-based immutability policies. Preventing this operation is unnecessary.
>
> **Overwriting existing documents:**  
> Overwriting an existing blob is prohibited when legal hold is active or a time-based immutability policy applies. Overwriting would fail under the described condition. This operation should be prevented.


- https://chatgpt.com/share/67469a77-327c-8000-8c21-03dfab9101c8
- https://learn.microsoft.com/en-us/azure/storage/blobs/immutable-storage-overview#legal-holds

---

### Q136
**You provisioned an Azure Cosmos DB for NoSQL account named account1 with the default consistency level.  
You plan to congure the consistency level on a per request basis. The level needs to be set for consistent prex for read and write operations to account1.  
You need to identify the resulting consistency level for read and write operations.  
Which levels should you congure?**

- Read operations
    - strong
    - session
    - [consistent prefix](#q136)

- Write operations
    - strong
    - [session](#q136)
    - consistent prefix


> **Default Consistency Level of Azure Cosmos DB:** When you provision an Azure Cosmos DB for NoSQL account, the default consistency level is typically set to **Session** unless explicitly changed.  
>
> Clients can override the default consistency level that is set by the service. The consistency level can be set on a per-request basis, which overrides the default consistency level set at the account level. Consistency can only be relaxed at the SDK instance or request level.  
> `Strong > Bounded staleness > Session > Consistent prefix > Eventual`   
> To move from weaker to stronger consistency, update the default consistency for the Azure Cosmos DB account.  
>
> Overriding the default consistency level only applies to reads within the SDK client. An account configured for strong consistency by default will still write and replicate data synchronously to every region in the account. When the SDK client instance or request overrides this with Session or weaker consistency, reads will be performed using a single replica.

- https://learn.microsoft.com/en-us/azure/cosmos-db/nosql/how-to-manage-consistency?tabs=portal%2Cdotnetv2%2Capi-async#override-the-default-consistency-level

---

### Q137
**You are developing an application to store millions of images in Azure blob storage. The images are uploaded to an Azure blob storage container named `companyimages` contained in an Azure blob storage account named `companymedia`.  
The stored images are uploaded with multiple blob index tags across multiple blobs in the container.
You must find all blobs whose tags match a search expression in the container.   
The search expression must evaluate an index tag named status with a value of `final`.  
You need to construct the GET method request URI.  
How should you complete the URI?**

**`https://SLOT_1.blob.core.windows.net/SLOT_2?restype=container&comp=blobs&where=SLOT_3`**

**Parameters:**
- Status='final'
- Status<='final'
- companymedia
- companyimages

> SLOT_1: This is the name of the storage account, which is `companymedia`.   
> SLOT_2: This is the name of the blob container, which is `companyimages`.    
> SLOT_3: This is the query for the `where` clause. It must filter blobs with an index tag `status` equal to `'final'`. Thus, it will be `Status='final'`.  
> Correct URI: `https://companymedia.blob.core.windows.net/companyimages?restype=container&comp=blobs&where=Status='final'`  
> 
> `restype=container`: Indicates that the operation is performed at the container level.
> `comp=blobs`: Specifies that the operation is related to listing blobs.
> `where=Status='final'`: Filters blobs with the tag `status` set to `final`.

- https://chatgpt.com/share/6746abaf-59c4-8000-b95a-3614f4df2b6a
- https://learn.microsoft.com/en-us/azure/storage/blobs/storage-manage-find-blobs?tabs=azure-portal#finding-data-using-blob-index-tags

---

### Q138
**You develop two Python scripts to process data.  
The Python scripts must be deployed to two, separate Linux containers running in an Azure Container Instance container group.   
The containers must access external data by using the Server Message Block (SMB) protocol. Containers in the container group must run only once.  
You need to congure the Azure Container Instance.   
Which conguration value should you use?**

**Configuration Settings:**
- External data volume
    - Secret
    - Empty directory
    - Cloned git repo
    - [Azure file share](#q138)

> To access external data using the SMB protocol, you need to use Azure Files, which supports SMB. This will allow the containers to mount the **Azure file share** and access the external data.

- Container restart policy
    - [Never](#q138)
    - Always
    - OnFailure

> Since the containers must run only once, the restart policy should be set to **Never**. This ensures that the containers will not restart after they finish execution.

- https://chatgpt.com/share/6746aead-f880-8000-9015-a32ba5240d62
- https://learn.microsoft.com/en-us/azure/storage/files/files-smb-protocol?tabs=azure-portal
- https://learn.microsoft.com/en-us/azure/container-instances/container-instances-restart-policy
- [Q032](#q032)

---

### Q139
**You are developing a static website hosted on Azure Blob Storage. You create a storage account and enable static website hosting.  
The website must support the following requirements:  
• Custom domain name  
• Custom header values for all responses  
• Custom SSL certicate  
You need to implement the static website.  
What should you congure?**

**Requirements:**
- Custom domain name
    - Blob index tags
    - [Azure Content Delivery Network (CDN)](#q139)
    - Cross-Origin Resource Sharing (CORS)
    - Azure Storage Service Encryption (SSE)

- Custom header values
    - Blob index tags
    - [Azure Content Delivery Network (CDN)](#q139)
    - Cross-Origin Resource Sharing (CORS)
    - Azure Storage Service Encryption (SSE)

- Custom SSL certificate
    - Blob index tags
    - [Azure Content Delivery Network (CDN)](#q139)
    - Cross-Origin Resource Sharing (CORS)
    - Azure Storage Service Encryption (SSE)

> Static websites have some limitations. For example, If you want to configure headers, you'll have to use Azure Content Delivery Network (Azure CDN) and  To enable HTTPS, you'll have to use Azure CDN because Azure Storage doesn't yet natively support HTTPS with custom domains.  

- https://chatgpt.com/share/6746b2ec-b5b4-8000-853d-ae2ca832b678
- https://learn.microsoft.com/en-us/azure/storage/blobs/storage-blob-static-website#mapping-a-custom-domain-to-a-static-website-url
- https://learn.microsoft.com/en-us/azure/storage/blobs/storage-blob-static-website#adding-http-headers

---

### Q140
**You are developing an inventory tracking solution. The solution includes an Azure Function app containing multiple functions triggered by Azure Cosmos DB.   
You plan to deploy the solution to multiple Azure regions.  
The solution must meet the following requirements:  
• Item results from Azure Cosmos DS must return the most recent committed version of an item.  
• Items written to Azure Cosmos DB must provide ordering guarantees.  
You need to congure the consistency level for the Azure Cosmos DB deployments.  
Which consistency level should you use?**

- consistent prefix
- eventual
- bounded staleness
- [strong](#q140)
- session

> Azure Cosmos DB offers five consistency levels, each providing different trade-offs between performance, availability, and consistency guarantees:  
> 1. **Eventual consistency:** Guarantees no ordering of operations; the data eventually becomes consistent. This does not meet the requirements as there are no ordering guarantees.  
> 2. **Consistent prefix:** Ensures that reads never see out-of-order writes. While this provides ordering guarantees, it does not guarantee the most recent committed version of an item.  
> 3. **Bounded staleness:** Guarantees a lag between writes and reads, within a bounded time or versions. This does not guarantee the most recent committed version of an item.  
> 4. **Strong consistency:** Guarantees linearizability, meaning every read returns the most recent committed version of an item and provides global ordering of writes. This meets the requirements for both the most recent committed version and ordering guarantees.   
> 5. **Session consistency:** Guarantees consistency for a single client session, but it doesn't apply globally across all regions.  
> Since the requirements specify **the most recent committed version** and **ordering guarantees**, **strong consistency** is the only option that satisfies both.
>
> **Key Points:**   
> Strong consistency ensures the highest level of consistency but has higher latency and is not available in multi-region write configurations (only in single write-region setups).  
> In multi-region setups, strong consistency can still be achieved for reads if they are routed to the same region where the write occurs.  

- https://chatgpt.com/share/6746c7fb-ef64-8000-bf94-e00332e512bb
- https://learn.microsoft.com/en-us/azure/cosmos-db/consistency-levels
- https://learn.microsoft.com/en-us/azure/cosmos-db/consistency-levels#write-latency-and-strong-consistency

---

### ~~Q141~~
**You are developing an application that runs in several customer Azure Kubernetes Service clusters. Within each cluster, a pod runs that collects performance data to be analyzed later. 
A large amount of data is collected so saving latency must be minimized.  
The performance data must be stored so that pod restarts do not impact the stored data. Write latency should be minimized.  
You need to congure blob storage.  
How should you complete the YAML conguration?**
```
apiVersion: storage.k8s.io/v1
kind: SLOT_1
metadata:
    name: data-store
provisioner: kubernetes.i/SLOT_2
parameters:
    skuName: Premium LRS
reclaimPolicy: SLOT_3
```

- SLOT_1
    - PodStorage
    - [StorageClass](#q141)
    - PersistentVolume
    - PersistentVolumeClaim

- SLOT_2
    - [azure-disk](#q141)
    - azure-file
    - portworx-volume
    - scaleio

- SLOT_3
    - local
    - [retain](#q141)
    - delete

> **SLOT_1: `StorageClass`**
> A StorageClass defines the storage type and parameters (like skuName) that can be used by PersistentVolumes. This is appropriate as we need to define a reusable storage configuration for the pods.  
> 
> **SLOT_2: `azure-disk`**
> Azure Disk provides low-latency, durable block storage, which is suitable for scenarios requiring minimal write latency.  
> azure-file would be more appropriate for file sharing but has higher latency compared to azure-disk.  
>
> **SLOT_3: `retain`**
>The reclaimPolicy determines what happens to the data when the pod is deleted. retain ensures that the data is preserved even if the pod or PersistentVolumeClaim is deleted, which aligns with the requirement to not lose performance data after pod restarts.

- https://chatgpt.com/share/6746e73a-7d70-8000-98cb-34dce84cf162

---

### Q142 - Case study
**<u>Background:</u>   
VanArsdel, Ltd. is a global office supply company. The company is based in Canada and has retail store locations across the world. The company is developing several cloud-based solutions to support their stores, distributors, suppliers, and delivery services.**  

**<u>Corporate website:</u>  
The company provides a public website located at http://www.vanarsdelltd.com. The website consists of a React JavaScript user interface, HTML, CSS, image assets, and several APIs hosted in Azure Functions.**

**<u>Retail Store Locations:</u>   
The company supports thousands of store locations globally. Store locations send data every hour to an Azure Blob storage account to support inventory, purchasing and delivery services. Each record includes a location identier and sales transaction information.**  

**<u>Inventory services:</u>  
The company has contracted a third-party to develop an API for inventory processing that requires access to a specic blob within the retail store storage account for three months to include read-only access to the data.**

**The application components must meet the following requirements:**

- **Corporate website:**  
    - **Secure the website by using SSL.**
    - **Minimize costs for data storage and hosting.**
    - **Implement native GitHub workows for continuous integration and continuous deployment (CI/CD).**
    - **Distribute the website content globally for local use.**
    - **Implement monitoring by using Application Insights and availability web tests including SSL certicate validity and custom header value verication.**
    - **The website must have 99.95 percent uptime.**

- **Retail store locations:**  
    - **Azure Functions must process data immediately when data is uploaded to Blob storage. Azure Functions must update Azure Cosmos DB by using native SQL language queries.**
    - **Audit store sale transaction information nightly to validate data, process sales nancials, and reconcile inventory.**

- **Delivery services:**  
    - **Store service telemetry data in Azure Cosmos DB by using an Azure Function. Data must include an item id, the delivery vehicle license plate, vehicle package capacity, and current vehicle location coordinates.**
    - **Store delivery driver profile information in Azure Active Directory (Azure AD) by using an Azure Function called from the corporate website.**

- **Security:**  
    - **All Azure Functions must centralize management and distribution of conguration data for different environments and geographies, encrypted by using a company-provided RSA-HSM key.**
    - **Authentication and authorization must use Azure AD and services must use managed identities where possible.**  

**Issues:**   

- **Retail Store Locations:**  
    - **You must perform a point-in-time restoration of the retail store location data due to an unexpected and accidental deletion of data.**
    - **Azure Cosmos DB queries from the Azure Function exhibit high Request Unit (RU) usage and contain multiple, complex queries that exhibit high point read latency for large items as the function app is scaling.**

**You need to implement the delivery service telemetry data.  
How should you congure the solution?**

**Cosmos DB Configuration:**
- API
    - [Core (SQL)](#q142)
    - Gremlin
    - Table
    - MongoDB

- Partition Key
    - [Item id](#q142)
    - Vehicle license plate
    - Vehicle package capacity
    - Vehicle location coordinates
  
> **Cosmos DB API: Core (SQL)**  
> The Core (SQL) API is the best choice for this scenario becausenIt supports Azure Functions accessing and querying data using native SQL queries, as required in the case study.
>
> **Partition Key: Item id**  
> There are a wide range of possible values (one unique item ID per item). Because there's a unique item ID per item, the item ID does a great job at evenly balancing RU consumption and data storage.  

- https://learn.microsoft.com/en-us/azure/cosmos-db/partitioning-overview#use-item-id-as-the-partition-key

---

- •