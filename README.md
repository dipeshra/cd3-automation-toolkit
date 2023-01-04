# cd3-automation-toolkit


[![License: UPL](https://img.shields.io/badge/license-UPL-green)](https://img.shields.io/badge/license-UPL-green) [![Quality gate](https://sonarcloud.io/api/project_badges/quality_gate?project=oracle-devrel_cd3-automation-toolkit)](https://sonarcloud.io/dashboard?id=oracle-devrel_cd3-automation-toolkit)

## Introduction
CD3 stands for Cloud Deployment Design Deliverable.
The CD3 Automation toolkit has been developed to help in automating the OCI resource object management. 
<br><br>
It reads input data in the form of CD3 Excel sheets and generates the terraform files instead of handling the task through the OCI console manually. The toolkit also reverse engineers the components in OCI back to the Excel sheet and Terraform configuration. This generated Terraform code can be used by the OCI Resource Manager or leveraged by the organisations’ CI/CD processes.
<br><br>
<img width="715" alt="Screenshot 2022-12-30 at 11 57 41 AM" src="https://user-images.githubusercontent.com/103475219/210041258-258601c4-dd1d-48a1-b6d7-df1bda764190.png">
<br><br>

`To ease the execution of toolkit, we have provided the steps to build an image which encloses the code base and its package dependencies. Follow the steps provided below to clone the repo and build the image.`
<br><br>

#### OCI Services Currently Supported by CD3
<img width="748" alt="Screenshot 2022-12-30 at 1 05 59 PM" src="https://user-images.githubusercontent.com/103475219/210046038-91acacfd-5d65-4bc3-a1a8-90d425d2e3d3.png">


## Getting Started

### Pre-requisites
* Git
* Any docker cli compatible platform such as Docker or Rancher.
* OCI Tenancy Access Requirement - 
Appropriate IAM policies must be in place for each of the resources that the user may try to create.
Minimum requirement for the user to get started is to have the ability to read to the tenancy.

### To clone the repo
* Open your terminal and change the directory to the one where you want to download the git repo.
* Run the git clone command as shown below:
       git clone https://github.com/oracle-devrel/cd3-automation-toolkit
* Once the cloning command completes successfully, the repo will replicate to the local directory. 

### To build an image

* Change directory to cd3-automation-toolkit(i.e. the cloned repo in your local).
* Run docker build -t cd3toolkit:${image_tag} -f Dockerfile --pull --no-cache .<br/>
<br  /><b>Note</b> : <i>${image_tag} should be replaced with suitable tag as per your requirements/standards.</i>

### To save the image (Optional)
* Run docker save cd3toolkit:${image_tag} | gzip > cd3toolkit_${image_tag}.tar.gz


### To run the CD3 container and exec into it
* Run docker run -it -d -v <path_in_local_system_where_the_files_must_be_generated>:/cd3user/tenancies <image_name>:<image_tag>
* Run docker ps
* Run docker exec -it <container_id> bash
<br><br>
Follow the toolkit docs i.e. from the section <i>"Configuring the Docker Container to connect to OCI Tenancy"</i> in 
<a href="https://github.com/oracle-devrel/cd3-automation-toolkit/blob/develop/cd3_automation_toolkit/documentation/user_guide/01%20CD3%20Automation%20Toolkit%20-%20End%20to%20End%20Process.pdf">CD3 Automation Tookit - End To End Process Documentation</a>. Please download the document from Github.
<br>
<i>CD3 Quick Start template can be found at <b><a href="https://github.com/oracle-devrel/cd3-automation-toolkit/blob/develop/cd3_automation_toolkit/example/CD3-CIS-template.xlsx">CD3 CIS Template</a></b></i>
<br>
<i>CD3 Sample Excel templates can be found at <b><a href="https://github.com/oracle-devrel/cd3-automation-toolkit/tree/develop/cd3_automation_toolkit/example">Excel Templates</a> </b></i>
<br>
<br>
<b>Note</b> : <i>The above steps have been tested on Windows (Git Bash) and MacOS.</i><br/>

## Contributing
This project is open source.  Please submit your contributions by forking this repository and submitting a pull request!  Oracle appreciates any contributions that are made by the open source community.

## License
Copyright (c) 2022 Oracle and/or its affiliates.

Licensed under the Universal Permissive License (UPL), Version 1.0.

See [LICENSE](LICENSE) for more details.

ORACLE AND ITS AFFILIATES DO NOT PROVIDE ANY WARRANTY WHATSOEVER, EXPRESS OR IMPLIED, FOR ANY SOFTWARE, MATERIAL OR CONTENT OF ANY KIND CONTAINED OR PRODUCED WITHIN THIS REPOSITORY, AND IN PARTICULAR SPECIFICALLY DISCLAIM ANY AND ALL IMPLIED WARRANTIES OF TITLE, NON-INFRINGEMENT, MERCHANTABILITY, AND FITNESS FOR A PARTICULAR PURPOSE.  FURTHERMORE, ORACLE AND ITS AFFILIATES DO NOT REPRESENT THAT ANY CUSTOMARY SECURITY REVIEW HAS BEEN PERFORMED WITH RESPECT TO ANY SOFTWARE, MATERIAL OR CONTENT CONTAINED OR PRODUCED WITHIN THIS REPOSITORY. IN ADDITION, AND WITHOUT LIMITING THE FOREGOING, THIRD PARTIES MAY HAVE POSTED SOFTWARE, MATERIAL OR CONTENT TO THIS REPOSITORY WITHOUT ANY REVIEW. USE AT YOUR OWN RISK..
