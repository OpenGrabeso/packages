# OpenGrabeso/packages

Central OpenGrabeso GitHub packages repository so that we can use a single resolver

SBT configuration using [sbt-github-packages](https://github.com/djspiewak/sbt-github-packages)
===============================================================================================

project/plugins.sbt
-------------------

`addSbtPlugin("com.codecommit" % "sbt-github-packages" % "0.3.1")`

build.sbt
---------

`resolvers += Resolver.githubPackages("OpenGrabeso", "packages")`


.gitconfig 
--------------------------------------------------------------------
This is a global file, located in your user profile / home directory

```
[github]
  actor = YourGitHubUserName
  token = yourgithubaccesstoken
```

You can create a token in [your GitHub settings](https://github.com/settings/tokens)

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
