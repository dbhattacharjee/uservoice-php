UserVoice PHP library for API connections
=========================================

This library allows you to easily:
* Generate SSO token for creating SSO users / logging them into UserVoice (http://uservoice.com).

Examples
========

Prerequisites:
* Suppose your UserVoice site is at http://uservoice-subdomain.uservoice.com/ and **USERVOICE\_SUBDOMAIN** = uservoice-subdomain
* **SSO\_KEY** = 982c88f2df72572859e8e23423eg87ed (Admin Console -> Settings -> General -> User Authentication)

SSO-token generation using uservoice library
--------------------------------------------

SSO-token can be used to create sessions for SSO users. They are capable of synchronizing the user information from one system to another.
Generating the SSO token from SSO key and given uservoice subdomain can be done by calling UserVoice.generate\_sso\_token method like this:

    <?php
      require_once('uservoice.php');

      $sso_token = UserVoice::generate_sso_token(USERVOICE_SUBDOMAIN, SSO_KEY, array(
        'display_name' => "John Doe",
        'email' => 'john.doe@example.com'
      ), 5*60); # the token will be valid for 5 minutes (5*60 seconds) by default

      echo 'https://' . USERVOICE_SUBDOMAIN . '.uservoice.com/?sso='.$sso_token."\n";

    ?>