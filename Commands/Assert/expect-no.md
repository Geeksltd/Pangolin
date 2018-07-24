#ExpectNo("text")



Searches the current page to ensure the text contained in quotation marks is not found. The "ExpectNo"
prefixed commands are commonly used to test scenarios where we expect failure. Like the 'Expect' command, it can be combined with other commands (row, link, field, etc.) It is generally bad practice to end a test case on an 'ExpectNo' command. For example, if you wanted to check that a Cancel button works, it would make sense to begin your test by starting to add something, clicking Cancel and then validating the Add didn't complete. e.g.

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
            Click("Add New Customer");
            Set("Name").To("John Smith");
            Click("Cancel");
            ExpectNoRow("John Smith");
        }
    }
}

```



However, if the Cancel button relocates the User to a different page or doesn't relocate the User at all, the
expect no command would still pass without issue. In the example above, it would be better to first validate that the User has been relocated to the User Page (for example, validate that the header is present) and then validate that the Customer row hasn't been saved.