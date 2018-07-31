# AtRow("text") or AtRow(rownumber)  



This command searches anywhere in the row for the text contained within the quotation marks or row index number. It does not have to be content in the first column, but you should try to make the reference (in quotation marks) as unique as possible so that it will always find the row you intend it to.
The 'AtRow' command can define the text of an item in a row, or the index of a row that appears in a HTML
table. It must also have an act command as the last part of the line of Pangolin script it appears on.

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
            LoginAs<Adminuser>();
            Click("Agencies");
            AtRow(That.Contains, "Working Group").Click("Edit");
            Set("Name").To("Edited");
            Click("Save");
            WaitForNewPage();
            AtRow(1).Expect(What.Contains, "Edited");
        }
    }
}
```

