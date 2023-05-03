<!---
 Licensed to the Apache Software Foundation (ASF) under one or more
 contributor license agreements.  See the NOTICE file distributed with
 this work for additional information regarding copyright ownership.
 The ASF licenses this file to You under the Apache License, Version 2.0
 (the "License"); you may not use this file except in compliance with
 the License.  You may obtain a copy of the License at

      http://www.apache.org/licenses/LICENSE-2.0

 Unless required by applicable law or agreed to in writing, software
 distributed under the License is distributed on an "AS IS" BASIS,
 WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
 See the License for the specific language governing permissions and
 limitations under the License.
-->
Testing [MRELEASE-1114](https://issues.apache.org/jira/browse/MRELEASE-1114)
======================

This repository is basically a copy of [maven-apache-parent](https://github.com/apache/maven-apache-parent) where:
- SCM has been changed to personal GH
- deploy target has been changed to local target/staging-deploy directory

This permits doing personal release tests with `maven-release-plugin` that update this personal GH and does not require repository.apache.org.

Anybody can fork this repository, update the SCM url to do personal tests of:

```
mvn release:prepare
mvn release:perform
```

to see the [MRELEASE-1114](https://issues.apache.org/jira/browse/MRELEASE-1114) issue during `release:perform` step:

```
[INFO] [INFO] --- gpg:3.0.1:sign (sign-release-artifacts) @ mrelease-1114 ---
[INFO] gpg: signing failed: No pinentry
[INFO] gpg: signing failed: No pinentry
[INFO] [INFO] ------------------------------------------------------------------------
[INFO] [INFO] BUILD FAILURE
[INFO] [INFO] ------------------------------------------------------------------------
[INFO] [INFO] Total time:  1.130 s
[INFO] [INFO] Finished at: 2023-05-03T02:47:31+02:00
[INFO] [INFO] ------------------------------------------------------------------------
[INFO] [ERROR] Failed to execute goal org.apache.maven.plugins:maven-gpg-plugin:3.0.1:sign (sign-release-artifacts) on project mrelease-1114: Exit code: 2 -> [Help 1]
[INFO] [ERROR] 
[INFO] [ERROR] To see the full stack trace of the errors, re-run Maven with the -e switch.
[INFO] [ERROR] Re-run Maven using the -X switch to enable full debug logging.
[INFO] [ERROR] 
[INFO] [ERROR] For more information about the errors and possible solutions, please read the following articles:
[INFO] [ERROR] [Help 1] http://cwiki.apache.org/confluence/display/MAVEN/MojoExecutionException
[INFO] ------------------------------------------------------------------------
[INFO] BUILD FAILURE
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  3.622 s
[INFO] Finished at: 2023-05-03T02:54:16+02:00
[INFO] ------------------------------------------------------------------------
[ERROR] Failed to execute goal org.apache.maven.plugins:maven-release-plugin:3.0.0:perform (default-cli) on project mrelease-1114: Maven execution failed, exit code: 1 -> [Help 1]
```

To init the gpg agent, just run `mvn -Papache-release deploy` to have an interactive signing session.

To get back to the failure, kill your gpg agent.
