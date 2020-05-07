# Jenkins Integration with github

## Overview of the project

In this project, Jenkins is integrated with github. In real world scenario, all the code is deployed in production system and is accessible to client. Before deploying to production system, this is checked in test system and the deployed to production.
So in this project, I have shown this setup with smaller range.

## Job for production system

### First give the git repository and Branch Specifier as ` */master `.

![gitprodurl](https://github.com/amalk-money/jenkinsProject/blob/master/screenShots/prodgiturl.png)

### Now give the trigger as POLL SCM so that it call continuously monitor repository and download the code when updated.

![prodtrigger](https://github.com/amalk-money/jenkinsProject/blob/master/screenShots/prodtrigger.png)

### Now Build Executive shell will copy the updated code to the ` prod_space ` location and the production system will collect it from that location.

![buildprod](https://github.com/amalk-money/jenkinsProject/blob/master/screenShots/buildprod.png)

### For deploying the production environment, we are using docker technology and used ` http image ` to create the environment. And to access the production page, locally access it with ` host-ip:8086 ` location.

![prodpage]( https://github.com/amalk-money/jenkinsProject/blob/master/screenShots/prodpage.png)

## Job for testing system

### First give the git repository and Branch Specifier as ` */dev ` because dev is my feature branch and all the updation features to be updated in dev branch.

![gittesturl](https://github.com/amalk-money/jenkinsProject/blob/master/screenShots/gittesturl.png)

### Now give the trigger as POLL SCM so that it call continuously monitor repository and download the code when updated.

![testtrigger](https://github.com/amalk-money/jenkinsProject/blob/master/screenShots/triggertest.png)

### Now Build Executive shell will copy the updated code to the ` test_space ` location and the production system will collect it from that location.

![buildtest](https://github.com/amalk-money/jenkinsProject/blob/master/screenShots/buildtest.png)

### For deploying the testing system, we are using docker technology and used ` http image ` to create the environment. And to access the production page, locally access it with ` host-ip:8087 ` location.

![prodpage]( https://github.com/amalk-money/jenkinsProject/blob/master/screenShots/testpage.png)


## Job for Quality Assurance system

### First give the git repository where the updations need to be updated. And gave the ` */dev ` Branch because the QA team will first check the testing system and if the code is perfect, it will be merged to master branch.

![gitmergeurl](https://github.com/amalk-money/jenkinsProject/blob/master/screenShots/giturlmerge.png)

### Now give the trigger as POLL SCM so that it call continuously monitor repository and download the code when updated.

![mergetrigger](https://github.com/amalk-money/jenkinsProject/blob/master/screenShots/mergetrigger.png)

### Now Build Post Build Action.
### Branch to push : to which branch you want to merge.
### Target Remote name : is the name of remote repository.
### And click the build now whenever the QA teams feels the code is perfect.

![publisher](https://github.com/amalk-money/jenkinsProject/blob/master/screenShots/gitpublisher.png)

### Finally production page will look like the test page after merging.
![mergeprod](https://github.com/amalk-money/jenkinsProject/blob/master/screenShots/mergeprod.png)
