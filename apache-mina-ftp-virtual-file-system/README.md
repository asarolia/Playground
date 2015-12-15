Creating a java based FTP service using a virtual file system
=========

The idea of this POC is to expose an FTP service that consumes a *virtual file system* instead of the OS native file system. The virtual file system is nothing else that a static class that encapsulates a HashMap of futbol teams and its players. Each team is considered a *virtual directory* and each team's player is considered a *virtual file*. For this POC request concurrency is not allowed since there is no lock over the HashMap (nevertheless it would be very easy to refactor the static class in order to suppor concurrent requests). Also, file (players) reading and writting functionallity is not implemented.

The project was coded uses Java and the [Apache Mina library](https://mina.apache.org/ftpserver-project/features.html). The project dependencies are directly included in the repo since I haven't created a gradle/maven/ant configuration.

Environment setup
---------

*   Install [Eclipse](https://eclipse.org/downloads/)
*   Add the jars located in the **\/lib** folder into the classpath
*   Download and install [FileZilla](https://filezilla-project.org/) client. You will use it for testing your service.

Info
---------

The credentials for logging into the FTP server are hardcoded in the Main class. Just FYI they are *username = tito* and *password = 7170*.

If you want to run the FTP service over the native OS file system just swap the comments between these lines:

```java
user.setHomeDirectory("/");
//user.setHomeDirectory(".\\tito");
```

And set the home directory to whatever path you want.

When using FileZilla for testing your service remember to refresh (f5) the remote directory in order to get the newest data and to discard the local cache.