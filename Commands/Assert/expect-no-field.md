# ExpectNoField("text")



This command searches the current page in focus to ensure that a HTML field with the text contained in
quotation marks is not found. The "ExpectNo" prefixed commands are commonly used to test scenarios where the business logic dictates that something should be unavailable to users.

e.g.

```C#
using Pangolin;
using Microsoft.VisualStudio.TestTools.UnitTesting;

namespace TestUITests
{
    [TestClass]
    public class Test : UITest
    {
        [TestMethod]
        public override void RunTest()
        {
            LoginAs<Clientuser>();
            Click("Banks");
            WaitToSeeHeader(That.Contains, "Candidate Details");
            Click("Edit");
            WaitToSeeHeader(That.Contains, "Candidate Details");
            ExpectField("Title");
            ExpectField(That.Contains, "First name");
            ExpectField(That.Contains, "Middle name");
            ExpectField(That.Contains, "Last name");
            ExpectField(That.Contains, "Date of Birth");
            ExpectField(That.Contains, "Telephone number");
            ExpectField(That.Contains, "Mobile number");
            ExpectNoField(That.Contains, "Email address");
            ExpectNoField(That.Contains, "Employee Number");
            ExpectNoField(That.Contains, "Nationality");
            Click("Cancel");
        }
    }
}
```

