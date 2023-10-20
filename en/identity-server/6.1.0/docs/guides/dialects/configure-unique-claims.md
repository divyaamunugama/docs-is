# Configure unique claims

WSO2 Identity Server can be configured to retain the uniqueness of user claims. This allows you to keep a user claim value as a unique value within all user stores.

Follow the steps below to configure WSO2 Identity Server.

1.  Open the `deployment.toml` file in the `<IS_HOME>/repository/conf` folder and add the following configurations.

    ``` toml
    [[event_listener]]
    id = "unique_claim_user_operation_event_listener" 
    type = "org.wso2.carbon.user.core.listener.UserOperationEventListener"
    name = "org.wso2.carbon.identity.unique.claim.mgt.listener.UniqueClaimUserOperationEventListener" 
    order = 2 
    enable = true
    ```

2.  Restart WSO2 identity server and access the Management Console (`https://<IS_HOST>:<PORT>/carbon`) .

3.  From the list of claims, select the claim you want to configure to keep it unique.

    ![select-claim-from-list]({{base_path}}/assets/img/guides/select-claim-from-list.png)

4.  Click **Edit** to open the claim edit page.

    ![claim-edite-window]({{base_path}}/assets/img/guides/claim-edite-window.png)

5.  Click `Add Claim Property` and add an additional claim property as follows.
    
    <table>
        <thead>
        <tr class="header">
        <th>Property Name</th>
        <th>Property Value</th>
        </tr>
        </thead>
        <tbody>
        <tr class="odd">
        <td>isUnique</td>
        <td>true</td>
        </tr>
        </tbody>
    </table>

    ![additional-claim-properties]({{base_path}}/assets/img/guides/additional-claim-properties.png)

6.  Finally, click `Update` to save the additional claim property.

Now you can check and verify the functionality by adding users with an existing claim value or updating the user claim value of an existing claim.