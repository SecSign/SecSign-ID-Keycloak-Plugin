Installation of the extension

Requirements
<ol class="big">
 	<li>A fully working Keycloak installation.</li>
 	<li>The extension as .jar-file (<a href="https://github.com/SecSign/SecSign-ID-Keycloak-Plugin/releases">Download here</a>)</li>
</ol>

<strong>Installation</strong>
<ol class="big" >
 	<li>Shutdown the Keycloak-Server</li>
        <li>Copy the .jar-file ("secsign-authenticator.jar") to the subfolder "providers" of the keycloak installation folder</li>
 	<li>Rebuild the Installation of keycloak with the command "kc.sh build" in the "bin" subfolder of keycloak
            This will not erase any settings, It justs loads all new found extensions to the system
        </li>
        <li>Afterwards start the server (e.g. with "kc.sh start" or "kc.sh start-dev")</li>
        <li>Login as admin to the keycloak console</li>
        <li>Choose the real that shoud be secured by the 2FA</li>
        <li>Open the "Authentication" settings</li>
        <li>If you already use an own flow, choose it. Else you need to create a Flow by copying an existing or creating a new one.</li>
        <li>In the execution order there has to be a step which identifies the User (e.g Username Password Form) in front of the SecSign ID Authenticator. In a new flow you can do it by "Add execution"</li>
        <li>Subsequently please add "SecSign ID" Authenticator" by "Add execution".</li>
        <li>If you added the authenticator, please change the "Requirement" to "Required", else 2FA can be skipped or is automatically skipped for users without a saved SecSign ID. <img style="width:100%;" src="https://www.secsign.com/wp-content/uploads/2022/07/flow.png" alt="Flow with SecSign ID Authenticator" /> </li>
        <li>If you own an on-premise SecSign ID server, you can choose "Config" on the right side on the option "Actions" and follow the help below on "Configuration"</li>
        <li>To use the created flow, choose "Bindings" and select your flow as the "Browser Flow" (for Login in the browser).</li>
        <li>In the tab "Required Actions" enable the checkbox at "Enabled" beside "SecSign ID", so users without a SecSign ID can create one on login.<img style="width:100%;" src="https://www.secsign.com/wp-content/uploads/2022/07/bindings.png" alt="Selection of the flow" /></li>
        

</ol>
Configuration of the extension

There are multiple configurations:
<ol class="big">
 	<li>In your created flow you can choose "Config" on the menu for "Actions", to setup your on-premise SecSign ID Server.
For this you need 3 settings:
<img style="width:100%;" src="https://www.secsign.com/wp-content/uploads/2022/07/config.png" alt="Config of the Secsign Authenticator" />
            <ul>
              <li><strong>SecSign ID Server URL:</strong>The URL of the on-premise SecSign ID Server. (e.g: https://idserver.yourcompany.com)</li>
              <li><strong>Pin Account User:</strong> The PinAccount, to use the server. This Application User needs access rights, to create SecSign IDs on the server.</li>
	      <li><strong>Pin Account Password:</strong> The password of the PinAccount, to use the server.</li>
            </ul>
</li>
 	<li>Furthermore you can change or add SecSign IDs of single users. For that navigate to the "Users" option on the keycloak admin console and choose the user to change the SecSign ID for. In the tab "attributes" you can add or change the attribute "secsignid".
        </li>
<img style="width:100%;" src="https://www.secsign.com/wp-content/uploads/2022/07/attributes.png" alt="Attributes of the user" />
</ol>

Procedure of Login
<ul>
<li>The user identifies in the first step, e.g. by entering username and password.</li>
<li>Afterwards there is a check, whether the user has a SecSign ID.</li>
<li>If the user already has a SecSign ID saved, the authentication is started for that.</li>

<li>If the user has no SecSign ID, one is created for him and the corresponding QR-Code is shown on the screen.
After scanning the QR-Code with the smartphone and creating the SecSign ID on the smartphone, the authentication is started automatically.
</li>

<li>On the next login, the user can use the SecSign ID immediately.</li>
</ul>
<img style="max-width:300px;vertical-align: top;" src="https://www.secsign.com/wp-content/uploads/2022/07/login-form.png" alt="Username und Password Login Form" /> <img style="max-width:300px;vertical-align: top;" src="https://www.secsign.com/wp-content/uploads/2022/07/qr.png" alt="QR-Code for creation of the SecSign ID" /> <img style="max-width:300px;vertical-align: top;" src="https://www.secsign.com/wp-content/uploads/2022/07/auth.png" alt="Auth-Process with SecSign ID" />


