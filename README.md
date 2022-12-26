<h1 align="center">
    Corona-Warn-App Parent POM
</h1>

<p align="center">
  <a href="#development">Development</a> •
  <a href="#documentation">Documentation</a> •
  <a href="#support-and-feedback">Support</a> •
  <a href="#how-to-contribute">Contribute</a> •
  <a href="#contributors">Contributors</a> •
  <a href="#repositories">Repositories</a> •
  <a href="#licensing">Licensing</a>
</p>

The goal of this project is to develop the official Corona-Warn-App for Germany based on the exposure notification API from [Apple](https://www.apple.com/covid19/contacttracing/) and [Google](https://www.google.com/covid19/exposurenotifications/). The apps (for both iOS and Android) use Bluetooth technology to exchange anonymous encrypted data with other mobile phones (on which the app is also installed) in the vicinity of an app user's phone. The data is stored locally on each user's device, preventing authorities or other parties from accessing or controlling the data. This repository contains the **parent pom** for the Corona-Warn-App.

## About this component

This project offers central management for dependencies within the CWA ecosystem.

The cwa-parent artifact will be declared as parent for all microservices.

```xml
<project>
    ...
    <parent>
        <groupId>app.coronawarn</groupId>
        <artifactId>cwa-parent</artifactId>
        <version>1.0</version>
    </parent>
</project>
```

In the microservices itself no explicit dependency version should be declared anymore. All versions will be configured and approved in this project.
This allows a better overview about the used components and a much more comfortable way to update dependencies.

To further simplify the structure of the pom.xml files of the microservices, this project introduces Dependency-Building-Blocks.
These building blocks are combining a set of dependencies to one dependency which needs to be included.

```xml
    <dependencies>
        <dependency>
            <groupId>app.coronawarn</groupId>
            <artifactId>cwa-parent-spring-boot</artifactId>
            <version>${project.parent.version}</version>
            <type>pom</type>
        </dependency>
    </dependencies>
```

The package ```cwa-parent-spring-boot``` will automatically Spring-Boot-Starter-Packages and Test Dependencies which were used in all microservices related to CWA.

A list of available building blocks can be found in pom.xml in root directory of this repository in the ```<modules>``` section.

### Build
Whether you cloned or downloaded the 'zipped' sources you will either find the sources in the chosen checkout-directory or get a zip file with the source code, which you can expand to a folder of your choice.

In either case open a terminal pointing to the directory you put the sources in. The local build process is described afterwards depending on the way you choose.

#### Maven based build
This is the recommended way for taking part in the development.  
Please check, whether following prerequisites are installed on your machine:
- [Open JDK 11](https://openjdk.java.net) or a similar JDK 11 compatible VM  
- [Maven](https://maven.apache.org)

## Documentation  
The full documentation for the Corona-Warn-App can be found in the [cwa-documentation](https://github.com/corona-warn-app/cwa-documentation) repository. The documentation repository contains technical documents, architecture information, and white papers related to this implementation.

## Support and feedback
The following channels are available for discussions, feedback, and support requests:

| Type                   | Channel                                                                                                                                                                                                                                  |
|------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| **General Discussion** | <a href="https://github.com/corona-warn-app/cwa-documentation/issues/new/choose" title="General Discussion"><img src="https://img.shields.io/github/issues/corona-warn-app/cwa-documentation/question.svg?style=flat-square"></a> </a>   |
| **Concept Feedback**   | <a href="https://github.com/corona-warn-app/cwa-documentation/issues/new/choose" title="Open Concept Feedback"><img src="https://img.shields.io/github/issues/corona-warn-app/cwa-documentation/architecture.svg?style=flat-square"></a> |
| **CWA-Parent issues**  | <a href="https://github.com/corona-warn-app/cwa-parent/issues" title="Open Issues"><img src="https://img.shields.io/github/issues/corona-warn-app/cwa-parent?style=flat"></a>                                                            |
| **Other requests**     | <a href="mailto:opensource@telekom.de" title="Email CWA Team"><img src="https://img.shields.io/badge/email-CWA%20team-green?logo=mail.ru&style=flat-square&logoColor=white"></a>                                                         |

## How to contribute  
Contribution and feedback is encouraged and always welcome. For more information about how to contribute, the project structure, as well as additional contribution information, see our [Contribution Guidelines](./CONTRIBUTING.md). By participating in this project, you agree to abide by its [Code of Conduct](./CODE_OF_CONDUCT.md) at all times.

## Contributors  
The German government has asked SAP AG and Deutsche Telekom AG to develop the Corona-Warn-App for Germany as open source software. Deutsche Telekom is providing the network and mobile technology and will operate and run the backend for the app in a safe, scalable and stable manner. SAP is responsible for the app development, its framework and the underlying platform. Therefore, development teams of SAP and Deutsche Telekom are contributing to this project. At the same time our commitment to open source means that we are enabling -in fact encouraging- all interested parties to contribute and become part of its developer community.

## Repositories

A list of all public repositories from the Corona-Warn-App can be found [here](https://github.com/corona-warn-app/cwa-documentation/blob/master/README.md#repositories).

## Licensing
Copyright (c) 2020-2023 Deutsche Telekom AG.

Licensed under the **Apache License, Version 2.0** (the "License"); you may not use this file except in compliance with the License.

You may obtain a copy of the License at https://www.apache.org/licenses/LICENSE-2.0.

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the [LICENSE](./LICENSE) for the specific language governing permissions and limitations under the License.
