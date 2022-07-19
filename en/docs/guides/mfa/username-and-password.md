# Configuring Multi-factor Authentication with Username and Password

This scenario involves obtaining the username first and validating that
prior to autenticating the user using the password.

## Prerequisites

- You need to [set up the sample]({{base_path}}/guides/adaptive-auth/adaptive-auth-overview/#set-up-the-sample) application.

## Configure MFA using basic authentiation

To configure mfa using username and password:

1. On the management console, go to **Main** > **Identity** > **Service Providers** > **List**.

2. Click **Edit** on the service provider you have created.

3. Expand the **Local and Outbound Authentication Configuration** section and click **Advanced Configuration**.

    !!! info
        see [Configuring Local and Outbound Authentication for a Service Provider]({{base_path}}/learn/configuring-local-and-outbound-authentication-for-a-service-provider) for more information.

    ![configure-local-outbound]({{base_path}}/assets/img/using-wso2-identity-server/configure-local-outbound.png)

6. Click **Add Authentication Step**. Then add a local authenticator from **Local Authenticators** section. Select **identifier** from the dropdown. This is used to identify the user.

    !!! note
        The identifier is not an authenticator, so having only
        the identifier in the authentication flow will fail the
        authentication. If there are no authenticators configured other than identifier, an error occurs when updating the service provider.


7. Click **Add Authentication step** and add the **basic**
    authenticator from **Local Authenticators** section.  This will
    enable the password as the 2nd step authenticator.  
    ![second-step-authenticator]({{base_path}}/assets/img/using-wso2-identity-server/second-step-authenticator.png)
8. Click the **Update** button. This navigates you to the previous
    screen with your newly configured authentication steps.

    !!! tip
        However, by default, the username is not validated and WSO2 Identity Server does not check whether it exists in the userstore. This can be configured by setting the following parameter in the
        `<IS_HOME>/repository/conf/deployment.toml` file as shown below.

        ``` toml
        [authentication.authenticator.user_identifier] 
        name ="IdentifierExecutor"
        enable=true
        [authentication.authenticator.user_identifier.parameters]
        validate_username= false
        ```

## Try it out

1. Access the following sample PickUp application URL:
    <http://localhost.com:8080/saml2-web-app-pickup-dispatch.com>
2. Enter the username and click **NEXT**.  
    ![enter-username]({{base_path}}/assets/img/using-wso2-identity-server/enter-username.png)
3. Enter the password and click **SIGN IN**.  
    ![enter-password]({{base_path}}/assets/img/using-wso2-identity-server/enter-password.png)

  
