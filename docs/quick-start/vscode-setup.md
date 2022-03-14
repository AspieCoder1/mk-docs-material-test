# Setup using Visual Studio Code
In this section, we will be going through the steps to setup the datapreparer tool to run in visual studio code.

## Prerequisites
Install the **Java** and **Extension Pack for Java** extensions. 

![Extension Pack for Java](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FP3MlUexSWXzBdI2MDVAl%2Fuploads%2FRudx2Iraj0PYYIGjdSh8%2Fimage.png?alt=media&token=cdd1a9d2-c5ca-42ff-bc93-9e1622ccdf5c){: .center}

## Creating a launch configuration
Head over to the **Run and Debug** extension on the left of your application.
Click on **create a launch.json file**. 

![Run and Debug extension](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FP3MlUexSWXzBdI2MDVAl%2Fuploads%2F2d7JFa8atefhAMoZVIH1%2Fimage.png?alt=media&token=c3be919d-f0bb-4103-9deb-ea4cd4e67777){: .center}

Select **Java**. A launch.json file should now be created for you.

![Select Java](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FP3MlUexSWXzBdI2MDVAl%2Fuploads%2F8mMhzaGDMgYLdSGeLPSi%2Fimage.png?alt=media&token=07e106ff-38b6-457d-a820-c7ec071fbeaf){: .center}

> **_NOTE:_** It should take a minute or two to generate this file.

Once it is created, go back to the **Run and Debug** extension. Click on the drop down menu and click **add configuration**.

![Add configuration](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FP3MlUexSWXzBdI2MDVAl%2Fuploads%2FLZ97ylfSJJmzF8Epinmp%2Fimage.png?alt=media&token=01e7ee9c-f879-4484-83fe-0cab284c60d7){: .center}

Add this configuration into your launch.js. Make sure that **vmArgs** is there.
```
{
    "type": "java",
    "name": "Launch Data Preparer",
    "request": "launch",
    "mainClass": "com.tdvf.app.Main",
    "projectName": "datapreparer",
    "vmArgs": "-Xms768m -Djava.awt.headless=false -Dapple.awt.UIElement=true -Dtextdb.allow_full_path=true"
}
```
![launch.json](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FP3MlUexSWXzBdI2MDVAl%2Fuploads%2FpwL7ATlA7Lz7VSG3ykR0%2Fimage.png?alt=media&token=bb0daeb7-5573-4c9f-91c4-6b65d81b1088){: .center}

## Run the Datapreparer app
Go back to the Run and Debug extension and select Launch Data Preparer, then click on the green start button. 

![Run the app](https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2FP3MlUexSWXzBdI2MDVAl%2Fuploads%2FxoC7HF6K5QDf8KA1MmXV%2Fimage.png?alt=media&token=fb81fef5-2a33-485c-8511-24425fe3d218){: .center}

> **_NOTE:_** These steps should work for Windows, WSL, Linux and MacOS