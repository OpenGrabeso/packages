# OpenGrabeso/packages

Central OpenGrabeso GitHub packages repository so that we can use a single resolver

You will need your GitHub access token. You can create one in [GitHub settings](https://github.com/settings/tokens)


SBT configuration using [sbt-github-packages](https://github.com/djspiewak/sbt-github-packages)
===============================================================================================

project/plugins.sbt
-------------------

`addSbtPlugin("com.codecommit" % "sbt-github-packages" % "0.3.1")`

build.sbt
---------

```
resolvers += Resolver.githubPackages("OpenGrabeso", "packages")

githubTokenSource in ThisBuild := TokenSource.GitConfig("github.token") || TokenSource.Environment("GITHUB_USERTOKEN") || TokenSource.Environment("GITHUB_TOKEN")
```

.gitconfig 
--------------------------------------------------------------------
This is a global file, located in your user profile / home directory

```
[github]
  actor = YourGitHubUserName
  token = yourgithubaccesstoken
```


Maven configuration
===================

.m2/settings.xml
----------------

This is a global file, located in the .m2 subfolder of your user profile / home directory

```
<settings xmlns="http://maven.apache.org/SETTINGS/1.0.0"
  xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
  xsi:schemaLocation="http://maven.apache.org/SETTINGS/1.0.0
                      https://maven.apache.org/xsd/settings-1.0.0.xsd">
  <servers>
    <server>
      <id>github</id>
      <username>YourGitHubUserName</username>
      <password>yourgithubaccesstoken</password>
    </server>
  </servers>
</settings>
```

SBT configuration (does not seem to work, use sbt-github-packages)
=================

.github.credentials
------------------------
This is a global file, located in your user profile / home directory

```
realm=github
host=www.github.com
user=YourGitHubName
password=yourgithubaccesstoken
```

build.sbt
---------

```
resolvers in ThisBuild += "GitHub OpenGrabeso Apache Maven Packages" at "https://maven.pkg.github.com/OpenGrabeso/packages/"

credentials in ThisBuild += Credentials(Path.userHome / "github.credentials")
```

