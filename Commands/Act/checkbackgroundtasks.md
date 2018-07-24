#CheckBackgroundTasks();



Explanation - Redirect the current page to the page with the list of all Automated Tasks implemented in the
application
Usage - used to trigger an Automated Task
e.g. If there a task is used to send automatic emails, your code might look something like

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
            CheckBackgroundTasks();
            WaitForPopup();
            Click("Send Automatic Emails");
            WaitToSee(What.Contains, "Done: Send Automatic Emails");
            ClosePopup();
        }
    }
}

```

Please note, that the term above 'Send Automatic Emails' may be different from project to project and is the developers choice so your tests will need to be updated to match them