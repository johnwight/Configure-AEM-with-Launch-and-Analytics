# Configure-AEM-with-Launch-and-Analytics
Connect your Adobe Experience Manager Instance with Launch

The following instructions provide guidance on configuring Adobe Experience Manager (AEM) with Adobe Launch. Although your AEM site may differ from the example site used below, you can use these steps as a guide for setting up your own configuration.

Adobe Launch is the next generation of Dynamic Tag Management. It provides a platform-based approach to building Dynamic Tag Management (DTM) extensions and a streamlined distribution system to quickly deploy client-side DTM libraries. Custom resources can now be created and reused within DTM to simplify the distribution of client side web applications.

These instructions include the following sections:

1. [Setup Adobe Launch](#Launch)

1. [Configure with AEM 6.4](#64)

1. [Configure with AEM 6.3](#63)

## <a name="Launch">Setup Adobe Launch</a>

To Setup Adobe Launch:


1. On www.launch.adobe.com, click **New Property**.

     ![create new property](https://user-images.githubusercontent.com/29133525/35232042-a62c732e-ff57-11e7-9210-1205d6d9e46c.png)

1. On the **Create Property** box, provide the details for the new property and click **Save.**

     ![create property box details](https://user-images.githubusercontent.com/29133525/35232087-c8a33c3a-ff57-11e7-82ff-8b68c085726a.png)

1. Click the **Extensions** tab and install the Analytics extensions

1. Click on **Adobe Analytics** extension.

1. Enter your Adobe Analytics Report Suite ID in the corresponding report suites environments, such as *Production Report Suites*. If you do not have separate environments then please add the same report suite ID for all environments.

1. If you do not know how to find the Report Suite ID, login via Marketing Cloud in [Analytics](https://sc.omniture.com/login/), click **Admin >Report Suites** and create a new report suite or copy an ID of an existing report suite that you want to use.

     ![report suite manager](https://user-images.githubusercontent.com/29133525/36569650-db65b292-17eb-11e8-8684-2f36149c1185.png)


1. Click **Save** after entering the Report Suite ID as shown below.

     ![report suite id](https://user-images.githubusercontent.com/29133525/36569553-7b0ff7d6-17eb-11e8-8b18-83daa8f0da13.png)


1. Make sure you have the following extensions:

     ![final extensions](https://user-images.githubusercontent.com/29133525/36569456-1c087e34-17eb-11e8-8507-134971212aa9.png)


1. Click the **Rules** tab and click on **Create New Rule**.


1. Enter the rule name as **Analytics** and click the **Add** button under **EVENTS**.

     ![events](https://user-images.githubusercontent.com/29133525/36569035-5db319b8-17e9-11e8-92ba-0a2188ac50c8.png)


1. Specify the **Event Configuration** options as shown below and click **Keep Changes**.

     ![event config options](https://user-images.githubusercontent.com/29133525/36568862-d01f045e-17e8-11e8-9b75-8ff97818f087.png)


1. Click the **Add** button in the **Actions** section and specify the following options to **Send Beacon**. Click **Keep Changes**.

     ![action options](https://user-images.githubusercontent.com/29133525/36568770-75db8436-17e8-11e8-9396-258793def233.png)


1. Make sure your final Rule definition appears as shown below. Click **Save**.

     ![rule definition](https://user-images.githubusercontent.com/29133525/36568682-236d3460-17e8-11e8-9fa6-3b78c33bcafa.png)


1. Click the **Adapters** tab, then click **Add Adapter** and then create an **akamai** adapter as shown below.

     ![akamai adapter](https://user-images.githubusercontent.com/29133525/36568647-fca2aec8-17e7-11e8-91cf-b72d8028d838.png)


1. Click the **Environments** tab, then click **Add Environment** and create Dev, Stage, and Production environments.

     ![environments tab](https://user-images.githubusercontent.com/29133525/36568391-0feaf6ee-17e7-11e8-8f0a-441c647d3a1d.png)



1. Save the rule and click the **Publishing** tab. Click **Add New Library**.

     ![add new library](https://user-images.githubusercontent.com/29133525/36568300-b6863eec-17e6-11e8-833c-4c1281cc3859.png)


1. Provide a **Name** for the build, select the Dev (Development) environment, and then click **Add All Changed Resources**.

     ![provide build name](https://user-images.githubusercontent.com/29133525/36568047-d72503e6-17e5-11e8-8721-3d81ad67198c.png)


1. Build for development and staging and then approve for production.

     ![approve](https://user-images.githubusercontent.com/29133525/36567904-4def5bda-17e5-11e8-982f-018ed830170d.png)












Option 1: Launch with AEM 6.4
Go to https://console.adobe.io

Click on "New Integration".



Select "Access an API" and click on continue.



Select "Launch, by Adobe" and click on continue.



Select "New Integration" for fresh setup and click on continue.



Open the AEM instance in new window (http://localhost:4502) click on "Tools"->Security→Adobe IMS Configurations.



Create new Adobe IMS Configuration certificate as shown in below screenshot.



Download the public key certificate by clicking on "Download Public Key", this certificate needs to be uploaded in the I/O console integration.





Come to I/O Console Integration window upload the downloaded AEM-Adobe-IMS.crt in Public Key Certificates.



Copy the Client ID, Client Secret from Overview and the JWT Payload and Authorization Server info from "JWT" tab.



Come back to the AEM IMS Configuration next step, fill out details from I/O Console integration. Save the configuration.



Go to AEM Instance->Tools→Cloud Services→Adobe Launch Configurations.



Create a new configuration under we-retail website. Select the IMS Config, company and property as shown below.



Go to AEM instance->Sites.



Select "Card View" from upper right corner and click on (info) properties icon.



Go to Advanced tab and select Cloud Configuration under Configuration.



Select the we-retail path and save & close the configuration.



Open the We-Retail website→Right click->Inspect→Click on Sources. You will see that the Launch scripts is getting fired and events are flowing in the designated report suite.








Option 2: Launch with AEM 6.3
AEM 6.3 doesn't have the official connector for Launch. To connect your AEM 6.3 instance with Launch you can follow the below work around:

Go to your DTM account. (dtm.adobe.com)

Create a dummy empty property "Adobe_Launch". Please do not customize this property as we are not going to use it in our integration.



Go to AEM 6.3 instance. (e.g. http://localhost:4502/) click on "Tools" (Left panel->The hammer icon).



4. Go to "Deployment" and click on "Cloud Services".



5. Locate "Dynamic Tag Management" and click "Configure Now".



6. Provide Title and Name for configuration and click on Create.



7. Go to your Dynamic Tag Management profile. Click on DTM Account and copy the API Token.



8. Paste the API token to AEM→DTM Configuration window and click "Connect To DTM".





9. Select company and the dummy property that we created in step 2.



10. Click on Staging Settings and Production Settings and uncheck the "Use Self Hosting".



11. Go to Launch->Environments→Staging and copy the header code and replace it in AEM→DTM Configuration Staging Settings Header code section.



12. Go to Launch->Environments→Production and copy the header code and replace it in AEM→DTM Configuration Production Settings Header code section. Click Ok.



13. After the configuration it should look like this. Ensure that the scripts are the ones from Launch environments.



14. Go to AEM instance (http://localhost:4502/) and click on Sites.



15. Open the page in "Card View" from the upper right corner.



16. Click on the "Properties" icon (info) for the website which you want to connect to Launch.



17. Go to Cloud Services→Add Configuration→Select Dynamic Tag Management



18. Select the Launch integration you created in previous steps. Click Save and Close.



19. Open the We-Retail website→Right click->Inspect→Click on Sources. You will see that the Launch scripts is getting fired and events are flowing in the designated report suite.


