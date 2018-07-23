#Migrating from Sanity to Pangolin

## Where are my .Sanity files?
To export a project’s tests from SanityHub.com into *.Sanity files, in Sanity Studio click “Export to folder” from “Import” menu. 
 
## Conversion
The converter tool is located at R:\Tools\Sanity\SanityToPangolin.
 
### Sanity exported folder
This is the input folder for the application which is where you previously exported your sanity test files. So this folder is expected to contain *.Sanity files (or subfolders) for a project.
 
### Destination folder
This is the output folder for the convertor tool. It should be an empty folder, ideally named “Tests” and inside your project’s solution root folder. It’s where it will generate C# files (Pangolin tests) that are equivalent of each *.Sanity file.
 
### Convert button
When you click “Convert”, a new .csproj file will be created, which is of type Visual Studio Unit Test project. Then every .sanity file in the input folder will be converted to a .cs file in the output folder and then automatically included in the project (.csproj)
 
### BaseUrl (App.Config): 
The exported folder from Sanity contains a file named baseUrls.txt which simply contains the URL of the runnable test app. The convertor will transfer the contents of that file (which is just a URL) to a newly generated app.config file in the destination, so it’s available at runtime.

## Build
1. Go to destination folder and open the project in Visual Studio.
1. Create folder Uploadable.Files at the root of project and copy all files that are required in the uploader control, then set “Build Action” to “Embedded Resource” from “Properties” for each of them.
1. In the Package Manager update the Nuget package of Pangolin to the latest version.
1. Build the project.
