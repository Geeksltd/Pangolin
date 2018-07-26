# Click("text")



Activates the Left Mouse Button on any HTML element. It can be combined with other commands to be more precise (e.g. ClickButton(); or ClickLink();).

Add the label of whatever you want t o click after the command. e.g. ClickButton("Add New Customer"). Can also be used to click html elements without labels, 'ClickCheckbox();'

e.g. The following code shows different type of click commands:

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

            Click("Configurations");
            ClickButton("General");

            AtRow(That.Contains, "2014/2015").Column(That.Contains, "Months").ClickLink();
            WaitToSeeHeader(That.Contains, "MONTHS");
            AtRow("Apr").Column("Start date").Expect(What.Contains, "01/04/2014");
            
            AtRow(That.Contains, "Apr").Column(That.Contains, "Edit").ClickLink();
            WaitToSeeHeader(That.Contains, "Month details");
            AtLabel("Month").ClickField();
            Type("Edited Apr");
            ClickCheckbox("IsActive");
            ClickRadiobox("Monthly");
            Set("Start date").To("02/04/2014");
            Set("End date").To("25/04/2014");
            ClickButton("Save");
        }
    }
}

```

You can see how to use different types of click commands in above example.