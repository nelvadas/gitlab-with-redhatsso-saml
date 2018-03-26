# Authenticating Gitlab CE users with Red Hat SSO 
# Table of contents
 1. [Introduction](#introduction)
 2. [Gitlab CE Setup](#gitlabcesetup1)
 3. [RH SSO config](#rhsso)
    1. [RHSSO Install](#rhssoinstall)
    2. [SAML Configuration](#saml) 
       1. [SAML Client](#samlclient)
       2. [mapping](#mapping)
       3. [Adding RHSSO as SAML Provider in Gitlab](#gitlabrb)
 4. [GitlabCE SAML Authent](#testing)
 5. [Next](#next)

## Introduction <a name="introduction"></a>
Gitlab CE refers to the community edition of the popular source code management tool *Gitlab*.
On the devops journey, Clouds platforms like Openshift  enable developpers to create a custom Application Image from source code throughthe Source to image process: S2I.
Most often the source code is hosted in an external Git repository but more and more users are considering containerized platforms on Openshift Cluster.
Here come the security dilema with all it pitfalls: authorisations, authentification, etc..
In the following blog post series we will see how to secure a  containerired Gitlab instance with Red Hat SSO.
Red hat SSO support both SAML and OpenID Connect protocol, in the first part of this blog post series, we will 
Handle SAML interconnection; OpenID Connect will be handled in a separate blog post.

## Setup Gitlab CE <a name="gitlabcesetup1"></a>

You can start a custom CE gitlab instance by running the following docker command 

```
$ docker run -d  -p 7080:80  gitlab/gitlab-ce 

```
This  command pull the image gitlab/gitlab-ce: latest from docker hub and start a new dockerized  gitlab instance.
Browse your installation at [http://127.0.0.1:7080/](http://127.0.0.1:7080/) and fill the required admin details.
![Gitlab CE Installation](https://github.com/nelvadas/gitlab-with-redhatsso-saml/blob/master/images/gitlabce-install01.png)
Create a local admin acccount with the following credentials for example
```
New Password: P@ssw0rd
confirm New  Password:  P@ssw0rd
```
login with root/P@ssw0rd

![Gitlab CE Admin account](https://github.com/nelvadas/gitlab-with-redhatsso-saml/blob/master/images/gitlabce-install02.png)
you are now connected to the admin panel.
here we used a local account to logon, in the follwing section we will see how to enable SAML authentification through RHSSO


## Installing Red Hat SSO <a name="rhssoinstall"></a>
<a href="https://access.redhat.com/products/red-hat-single-sign-on#getstarted">RHSSO</a> provides Web single sign-on and identity federation based on SAML 2.0, OpenID Connect and OAuth 2.0 specifications.
RH SSO exists both in monolithic zip/tar or container images.
Install your prefer version and setup the basic admin account 

## SAML <a name="saml"></a>

### Create a gitlab-ce-saml client <a name="client"></a>
### Mappings <a name="mapping"></a>
### Adding RHSSO as SAML Provider in Gitlab.<a name="gitlabrb"></a>

## Tests <a name="testing"></a>
## OpenID Connect <a name="next"></a>
