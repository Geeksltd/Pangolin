# Batch running Pangolin tests on the cloud

## Pangolin Server App
You should install a hosted copy of the `Pangolin Test Orchestration` app on a server.
This should occur *only once for the whole company*.
The source code of the app is available at https://gitlab.com/basirjalali/Pangolin/tree/master/Pangolin/Pangolin.Orchestration.API 

Let’s say it’s hosted as https://pangolin.geeksltd.co.uk 

## Batch Run via Pangolin Test Explorer
To run a whole batch of unit tests on the cloud independently use the following command line utility:

```
Pangolin.Publisher.exe "C:\Projects\MyProject\Tests\bin\Debug\Tests.dll" "dd2fb66b-634d-4843-a1cb-6c83b47e2ee2" "https://pangolin.geeksltd.co.uk"
```

- The first argument is the full path to your Pangolin test project dll. 
- The second argument is the app id, it should be a GUID.
- The third argument must be the Pangolin Server url.

### Pangolin Test Explorer: Visual Studio Extension
The `Pangolin Test Explorer` extension has been provided to run batch of unit tests more convenience.
First of all, install the `Pangolin Test Explorer` extension via Visual Studio Extension tool.
Search for `Pangolin` extension in Extension tool or download it from Pangolin Test Explorer  and then install it.
After Installing, Pangolin Test Explorer appears in the Visual Studio menu under `View`/`Other Windows`/`PangolinWindow`. 

There is a Grid View to display the result of unit tests.

- Before you start running batch of unit tests, build the project and make sure the bin folder of `Pangolin.Publisher` has been copied to the path of `PangolinPublisherPath` value in the `App.config` file.
- Then click the button `New Batch Run`.
- While a whole batch of unit tests is running, the latest results will be displayed by clicking the `Refresh` button.
- To see the detail of a batch, click the `Started` column. Another window will be loaded to displays the details.
- The `Stop` column is provided to cancel running batch.

## Pangolin Server
> Note:This needs to be set up once only per organisation, and it already is, at http://pangolin.geeksltd.co.uk.

The Pangolin Server application is responsible for batch running a whole bunch of pangolin tests. It doesn’t run the tests itself, but rather creates a set of cloud virtual machines to execute the tests.

If required, to set it up on a new server on AWS, follow these instructions step by step:

1. Create a VM in Amazon, this one must be Windows Server with SQL Server.
1. In AWS create an Elastic IP to that VM.
1. Map a domain (e.g. pangolin.geeksltd.co.uk) to that IP.
1. Log in to the VM server.
1. From the Pangolin source, copy `Pangolin.CloudManager` to the server under `C:\Projects`.
1. Open the `Pangolin.CloudManager` console application and set these `App.config` keys:
   1. AmazonAccessKeyId : ….
   1. AmazonSecretAccessKey: ...
   1. AmazonPangolinImageId: *{Use the ID you will create in the next step}*
1. Enable IIS by adding the IIS feature.
1. From the Pangolin source, copy `Pangolin.Orchestration.API` to the server under `C:\Projects`
1. Grant `IIS_USRS` full control permission on that folder.
1. Open IIS and add a website for that folder, bind to the domain (e.g. pangolin.geeksltd.co.uk)
1. Set up SSL (see https://training.geeksltd.co.uk/a/CL/ALN).
1. Modify these keys from Web.config to update these settings:
   1. `ConnectionString`: *{database connection string}*
   1. `PangolinCloudManagerPath`: *C:\Projects\Pangolin.CloudManager*
   1. `PangolinRunnerServers`: *{number of server to be created}*



