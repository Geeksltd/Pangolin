#Run<T>()  (Preconditions)



The command "Run<T>()" includes in your test case another test case from the same project. This is helpful for setting up your application before you execute your test. For example, if you wanted to login with a
particular User, you might need to create that User first. If you wanted to use a particular Company in your test, you need to run a test to add that Company. "T" is a generic class which should be another test case that inherited UITest class, runs that test first. We call these preconditions.

There can be many levels to preconditions. A precondition can have its own preconditions and so on. Pangolin will ignore any duplicate tests in preconditions so this prevents any duplicate data. For example, if I want to add 2

Doctors to a test case, I might have 2 tests called

Add New Doctor: Daniel Doctor
Add New Doctor: Danielle Doctor

Each test contains the same precondition that adds their Hospital (Add New Hospital: Homerton Hospital).
Running each test by themselves would give no error but running both as 2 preconditions would add the
Hospital twice, potentially causing an error. However, Pangolin sees that it is a duplicate and makes sure to run it only once, therefore my new test will have 2 doctors in the system to use