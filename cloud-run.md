# Batch running Pangolin tests on the cloud

## Pangolin Server App
You should install a hosted copy of the `Pangolin Test Orchestration` app on a server.
This should occur *only once for the whole company*.
The source code of the app is available at https://gitlab.com/basirjalali/Pangolin/tree/master/Pangolin/Pangolin.Orchestration.API 
 
Let’s say it’s hosted as https://pangolin.geeksltd.co.uk 

## Batch Run via Pangolin Test Explorer
To run a whole batch of unit tests on the cloud independently use the following command line utility:

```
Pangolin.Publisher.exe “C:\Projects\MyProject\Tests\bin\Debug\Tests.dll" https://pangolin.geeksltd.co.uk
```
 
- The first argument is the full path to your Pangolin test project dll. 
- The second argument must be the Pangolin Server url.
 
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
