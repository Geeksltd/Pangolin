## Fresh state: Server side compatibility

Running a test will often change the state (database, files, cookies, etc).
On the other hand, every time that you run any test, it should execute against a known and predictable state.

### With Docker/Containers

If you use Containers such as Docker, at the beginning of each test you should create a fresh container.
After a test is executed, you discard its container (which has dirty state). And the next test will again run in a fresh container, that is made from the source image. The source image will always have a known and predictable state.

### Without Docker/containers

If you don't use containers, and instead run the web application natively on Windows, then you need to provide Pangolin with a mechanism to reset the application to a known state.

1. Your application database should be avilable as SQL scripts in a folder that the application run-time can access.
2. Upon start-up, your application should create its database from the script files.
3. You should provide a way for Pangolin to explicitly ask your application to discard the current dirty database and start a fresh one from the script files again. To achieve this, Pangolin will send the following HTTP request to your application at the beginning of running each new test:

> http://localhost:1234/?Web.Test.Command=restart

This is already supported in the M# and Olive frameworks. If you use any other framework, you need to add a http handler that responds to that command and does the following:

- Recreate the database
- If you use files, clean up and recreate from a read-only source
- Clear browser cookies
- Clear database cache and any other application cache
- Clear any other state you might be using in your application.