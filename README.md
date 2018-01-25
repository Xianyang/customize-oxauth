# jettybackup

### How to use
When Gluu Server is installed and you want to configure the User Interface of login/enroll/authenticate page, pull these folders to `/opt/gluu/jetty/oxauth/custom/`

Among those files

* `/pages/login.xhtml` will modify the default login page
* `/pages/auth/super-gluu/login.xhtml` will modify the enroll/authenticate pages using super gluu

Instructions by gluu server are here: [https://gluu.org/docs/ce/3.1.2/operation/custom-design/](https://gluu.org/docs/ce/3.1.2/operation/custom-design/)

### Steps to customize UI

#### Changes on website
1. `manage custom scripts` -> `super gluu` -> `label` to `PwC FIDO Demo`
2. `organization configuration` -> `OxTrust Settings`, add organization logo and organization favicon

#### Changes on oxauth
Just pull this repository to `/opt/gluu/jetty/oxauth/custom/`. It will automatically complete the step below
1. add `/pages/login.xhtml` and `/pages/auth/super-gluu/login.xhtml`

#### Changes on identity
1. To change the **GLUU** label on the log out page, add `finishlogout.xhtml` to `/opt/gluu/jetty/identity/custom/pages` from `/opt/jetty-version/temp/jetty-localhost-8082-identity.war-RANDOM/webapp/finishlogout.xhtml`. Then modify **GLUU** to **PwC FIDO Demo**.
2. To change `Welcome to your Gluu Identity Appliance 3.1.1.Final ! ` in the home page, add `home.xhtml` to `/opt/gluu/jetty/identify/custom/pages` from `/opt/jetty-version/temp/jetty-localhost-8082-identity.war-RANDOM/webapp/home.xhtml`. Then modify `value="#{msg['home.welcome']}"` to `value="Welcom to PwC FIDO Demo"`
3. To change `title` and **GLUU Identity Appliance**, we need to modify original file in `/opt/gluu/jetty/identity/webapp/identity.war`.
- install jdk first [https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-debian-8](https://www.digitalocean.com/community/tutorials/how-to-install-java-with-apt-get-on-debian-8)
- unpack identity.war using `jar xvf identity.war`
- modify `template.xhtml`, `newtemplate.xhtml` and `fullWidthEmpty.xhtml` in `/opt/jetty-version/temp/jetty-localhost-8082-identity.war-RANDOM/webapp/WEB-INF/incl/layout/`. Find `<title>#{organizationService.organization.organizationTitle}</title>`, change it to `<title>PwC</title>`
- modify `oxtrust.properites` and `oxtrust_en.properties` in `/opt/jetty-version/temp/jetty-localhost-8082-identity.war-RANDOM/webapp/WEB-INF/classes/`. Find `leftmenu.gluIdentityApplicance`, change its value to `PwC FIDO Demo`.
- pack identity.war using `jar -cvf identity.war *`, put it back to where it is.
- run `service identity restart`
