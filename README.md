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
Testing MRELEASE-1114
======================

This repository is basically a copy of [maven-apache-parent](https://github.com/apache/maven-apache-parent) where:
- SCM has been changed to personal GH
- deploy target has been changed to local target/staging-deploy directory

This permits doing personal release tests with `maven-release-plugin` that update this personal GH and does not require repository.apache.org.
