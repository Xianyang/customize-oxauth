# jettybackup

### How to use
When Gluu Server is installed and you want to configure the User Interface of login/enroll/authenticate page, pull these folders to `/opt/gluu/jetty/oxauth/custom/`

Among those files

* `/pages/login.xhtml` will modify the default login page
* `/pages/auth/super-gluu/login.xhtml` will modify the enroll/authenticate pages using super gluu

Instructions by gluu server are here: [https://gluu.org/docs/ce/3.1.2/operation/custom-design/](https://gluu.org/docs/ce/3.1.2/operation/custom-design/)

### Steps to customize UI

1. `manage custom scripts` -> `super gluu` -> `label` to `PwC FIDO Demo`
2. `organization configuration` -> `OxTrust Settings`, add organization logo and organization favicon
3. add `/pages/login.xhtml` and `/pages/auth/super-gluu/login.xhtml`
4. add and modify **GLUU** in `finishlogout.xhtml` in `identity/custom/pages`
