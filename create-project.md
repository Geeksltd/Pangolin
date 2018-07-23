# Creating a Pangolin test project
For a new project which does not have existing sanity tests, follow the following instructions:

1. In the project’s solution in Visual Studio, create new *Unit Test* project called *Tests*
1. Create folder Uploadable.Files at the root of project and copy all files that are required in the uploader control, then set “Build Action” to “Embedded Resource” from “Properties”  for each of them.
1. Add latest version of Pangolin nuget
1. .... (TODO: Complete)

### Create your first TestClass using the following pattern:

```c#
using Pangolin;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace Test
{
	[TestClass]
	public class TestCaseName : UITest
	{
        	[TestMethod]
       	public override void RunTest()
        	{

              	//YOUR CODE
        	}
	}
}
```
