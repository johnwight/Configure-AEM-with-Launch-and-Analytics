# Configure-AEM-with-Launch
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

1. Click the **Extensions** tab and install the **Analytics** extension.

      ![extensions](https://user-images.githubusercontent.com/29133525/35232128-ee66002e-ff57-11e7-9958-5aa36d633d26.png)


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




## <a name="64">Configure with AEM 6.4</a>

To configure Launch with AEM 6.4:

1. On the [Adobe I/O Console](https://console.adobe.io), click **New Integration**.


1. Click **Access an API** and then click **Continue**.

     ![access api](https://user-images.githubusercontent.com/29133525/36578831-faadb772-181c-11e8-9fbc-c9ce50a72e85.png)


1. Under **Experience Cloud**, select **Launch, by Adobe** and then click **Continue**.

     ![experience cloud](https://user-images.githubusercontent.com/29133525/36578923-7bf43072-181d-11e8-97f8-0504c22d063d.png)
     

1. Select **New Integration** for fresh setup and click **Continue**.

     ![new integration](https://user-images.githubusercontent.com/29133525/36578993-d80482f4-181d-11e8-9526-6c9fdab88e44.png)



1. In the [AEM instance](http://localhost:4502) in a new window and click **Tools > Security > Adobe IMS Configurations**.

     ![ims config](https://user-images.githubusercontent.com/29133525/36579116-a11b871e-181e-11e8-8b90-5d182a4158ac.png)


1. Create a new Adobe IMS Configuration certificate as shown below:

     ![ims cert](https://user-images.githubusercontent.com/29133525/36579164-e5475af8-181e-11e8-9004-50bc91c77303.png)


1. Download the public key certificate by clicking on **Download Public Key**. This certificate needs to be uploaded in the Adobe I/O console integration.

     ![download public key](https://user-images.githubusercontent.com/29133525/36579223-2c42eeea-181f-11e8-92f1-d9b51ce04245.png)



1. On the I/O Console Integration window, click **Select a file** and upload the **AEM-Adobe-IMS.crt** in Public Key Certificates.

     ![console integration](https://user-images.githubusercontent.com/29133525/36579313-99283e20-181f-11e8-9b43-2689e269f998.png)


1. On the **Overview** tab, copy the **Client ID** and **Client Secret**. Then copy the **JWT Payload** and **Authorization Server** info from **JWT** tab.

     ![credentials](https://user-images.githubusercontent.com/29133525/36579438-4ed66512-1820-11e8-9e19-ee8afb3e7c22.png)


1. Return to the AEM IMS Configuration step and provide the copied details from the I/O Console integration. Save the configuration.

     ![integration details](https://user-images.githubusercontent.com/29133525/36580153-424cd0c0-1824-11e8-85c4-eefd2f022403.png)


1. In your AEM Instance, click **Tools > Cloud Services >Adobe Launch Configurations**.

     ![adobe launch configurations](https://user-images.githubusercontent.com/29133525/36579566-f0bc04ae-1820-11e8-905d-13b171456feb.png)


1. Create a new configuration under the **We.Retail** website. Select the **Associated Adobe IMS Configuration**, **Company** and **Property** as shown below.

     ![new config](https://user-images.githubusercontent.com/29133525/36579614-3bda612e-1821-11e8-9f55-8c332678c054.png)


1. In your AEM instance, click **Sites**, then select **Card View** from upper right corner and click the info properties icon.

     ![card view](https://user-images.githubusercontent.com/29133525/36579659-7bbad698-1821-11e8-8098-74fbc797c27b.png)


1. On the **Advanced** tab, select **Cloud Configuration**.



1. Select the **We.retail** path and save & close the configuration.

     ![save path](https://user-images.githubusercontent.com/29133525/36579710-cca3116a-1821-11e8-92b0-9a6f05f37f22.png)


1. Open the We-Retail website. Right click and select **Inspect > Sources**. You will see that the Launch scripts are firing and events are flowing in the designated report suite.

     ![scripts fired](https://user-images.githubusercontent.com/29133525/36579751-0372e99a-1822-11e8-93db-1fc1d570abe5.png)



## <a name="63">Configure with AEM 6.3</a>

AEM 6.3 does not have the official connector for Launch. However, to connect your AEM 6.3 instance with Launch, you can follow work around presented below.

To configure Launch with AEM 6.3:


1. In your [DTM account](dtm.adobe.com), create a dummy empty property **Adobe_Launch**. Please do not customize this property as we are not using it in our integration.

     ![dummy report](https://user-images.githubusercontent.com/29133525/36580228-a2bae5dc-1824-11e8-8131-a5560b94ad79.png)



1. In your [AEM instance](http://localhost:4502/), click on **Tools** or the Hammer icon in the left panel.



1. In **Deployment,** click **Cloud Services**. 
     
     ![cloud services](https://user-images.githubusercontent.com/29133525/36580320-fb5ce708-1824-11e8-81d9-36fa2dad8885.png)

1. Locate "Dynamic Tag Management" and click "Configure Now".

     ![dtm](https://user-images.githubusercontent.com/29133525/36580397-4c421d64-1825-11e8-98ba-004392169dc3.png)


1. Provide a **Title** and **Name** for the configuration and click **Create**.



1. In your Dynamic Tag Management profile, click on the DTM Account and copy the API Token.

     ![copy token](https://user-images.githubusercontent.com/29133525/36580487-b4a47afa-1825-11e8-906d-0f03f0328283.png)


1. Paste the API token to AEM > DTM Configuration window and click **Connect To DTM**.

     ![paste](https://user-images.githubusercontent.com/29133525/36580572-0182bd78-1826-11e8-85a8-ce432e007aa8.png)
     ![connection successful](https://user-images.githubusercontent.com/29133525/36580641-4b063100-1826-11e8-8213-20f9502df972.png)


1. Select the company and the dummy property that you previously created.

     ![previous dummy](https://user-images.githubusercontent.com/29133525/36580703-95669bae-1826-11e8-9a11-bacbb596c069.png)


1. Click the **Staging Settings** and **Production Settings** tabs and uncheck the **Use Self Hosting**.

     ![staging](https://user-images.githubusercontent.com/29133525/36580800-ff3684cc-1826-11e8-8425-6ef32042c921.png)


1. In Launch > Environments > Staging, copy the header code and replace it in AEM > DTM Configuration Staging Settings Header code section.

     ![production](https://user-images.githubusercontent.com/29133525/36580849-3a12b2be-1827-11e8-9781-6f7d6cb9a214.png)


1. In Launch > Environments > Production, copy the header code and replace it in AEM > DTM Configuration Production Settings Header code section. Click **OK**.



1. After the configuring, it should appear as shown below. Nake sure the scripts are from Launch environments.



1. In your [AEM instance](http://localhost:4502/), click **Sites**, and open the page in **Card View** from the upper right corner.



1. Click the **Properties** icon for the website that you want to connect to Launch.



1. Click **Cloud Services > Add Configuration** and Select **Dynamic Tag Management**.



1. Select the Launch integration you created in previous steps. Click **Save & Close**.


1. Open the **We.Retail** website. Right click and select **Inspect > Sources**.  You will see that the Launch scripts are firing and events are flowing in the designated report suite.

## Authors
- Hiren Shah [@hirenshah111](https://github.com/hirenshah111).
- John Wight [@johnwight](https://github.com/johnwight).


## Feedback?

Please help make this solution as useful as possible. If you find a problem in the documentation or have a suggestion, click the **Issues** tab on this GiHhub repository and then click the **New issue** button. Provide a title and description for your comment and then click the **Submit new issue** button.

   ![submit new issue](https://user-images.githubusercontent.com/29133525/32515298-f344bd5a-c3bc-11e7-9978-34516f964f9f.png)


