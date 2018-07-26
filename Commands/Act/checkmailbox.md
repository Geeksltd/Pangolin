# CheckMailBox("email address")



The 'CheckMailBox' command accesses the email queue items in an application. This is basically a list of all the emails sent from the system to a specified email address. Typical scenarios that this command may be used is to receive registration confirmation links and password resetting instructions. After this, you can interact with the modal (pop up) window with the usual Pangolin commands.

e.g. After creating a user, likely you are going to reset the password. Here is an example:

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
            
            Click("Clients");
            Click("Users");
            WaitForNewPage();
            Click("New Client User");
            WaitForNewPage();
            Set("First Name").To("John");
            Set("Last name").To("Bupa");
            Set("Email address").To("JBupa@uat.co");
            AtLabel(That.Contains, "Roles").Click("Admin");
            Set("Telephone number").To("01234567890");
            Click("Save");
            WaitForNewPage();            
            AtRow(That.Contains, "John Bupa").Expect(What.Contains, "JBupa@uat.co");
            AtRow(That.Contains, "John Bupa").Expect(What.Contains, "01234567890");
            AtRow(That.Contains, "John Bupa").Expect(What.Contains, "Admin");
            
            CheckMailBox("JBupa@uat.co");
            WaitToSee(What.Contains, "Brookson Registration");
            
            Click("Registration");
            Click("Set Your Password");
            Set("Password").To("Test");
            Set("Confirm password").To("Test");
            Click("Set");
            WaitForNewPage();            
            Click("Proceed To The Login Page");
            WaitForNewPage();
            
            Set("Email address").To("JBupa@uat.co");
            Set("Password").To("Test");
            Above(What.Contains, "Forgot password?").Click("Login");
            WaitForNewPage();
            Expect(What.Contains, "John Bupa");
        }
    }
}
```

The above code shows how to use 'CheckMailBox' command, first creates a user and then resetting the password. it's important to go to the mail box page when resetting the password, called '?Web.Test.Command=testEmail' command to go to the new page.