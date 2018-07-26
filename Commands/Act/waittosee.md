# WaitToSee("text");



The execution of the next command is delayed until the element with the text matched in quotation has loaded. Also it can be used with other elements (e.g. WaitToSeeButton("text");, WaitToSeeHeader("text");, etc)..

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
            Click(The.Left, "Invoices");
            WaitToSeeHeader(That.Contains, "INVOICE");
            ExpectRow(That.Contains, "02/12/2015 20:00");
            WaitToSee("Approve");
            Click("Approve");
            WaitToSeeButton("OK");
            Click("OK");
        }
    }
}
```

