# InboxPager

![screenshot](https://github.com/itprojects/InboxPager/raw/master/img/1.png)

An E-mail client for the Android (java) platform. Supports imap, pop, and smtp protocols, through SSL/TLS.

# Download

You can download the application directly from GitHub by visiting ![this link](https://github.com/itprojects/InboxPager/tree/apk-direct).

Alternatively you can find [InboxPager](https://f-droid.org/repository/browse/?fdfilter=inbox&fdid=net.inbox.pager) in the F-droid app store.

# Usage

In order to use this application you have to enable SSL/TLS application-email-checking through your email account's web interface. Some email servers may have this feature already turned on (NOT GMAIL!, see below). If your account's server does not support this feature, it won't work.

Setting up an account in InboxPager happens through "Settings" > "Add Account". There, you have to enter your account's credentials, server parameters. If you don't know what your email account's server parameters are - try the automatic tools provided, otherwise enter and test your own configuration. Optionally, if you'd like to receive a sound or vibration notification tick those settings. If you wish to only refresh a specific account, when you individually choose to, then untick the "Allow in all-accounts-refresh".

By default InboxPager DOES NOT KEEP "FULL MESSAGE" copies of emails, instead, just gets the main textual contents of the message. If you wish to change this policy you can do this in the settings for individual account. In order to save email and/or attachments, the full message must be already in the internal database, or alternatively (re-)download the full message and then extract the attachment through the application. Be advised - keeping full messages can easily consume your device's internal memory.

# Features

The app can:

- Animate a smooth transition between visual contexts.

- Automatically convert texts from their declared character encoding to UTF-8. 

- Download your full email messages (with attachments inside).

- Download an individual attachment.

- Display server certificates used in the last connection.

- Keep track of your unread messages.

- Notify with sound of new messages, per user choice.

- Notify with device vibration of new messages, per user choice.

- Work with OpenPGP messages.

- Verify hostnames, if not self-signed certificates.

## WON'T FIX

- Automatically, on a cloud server, Save/Restore interrnal database. If a backup of the local device is necessary, then close the app and copy/paste the database from "/data/data/...".

- Backend that runs in the background.

- Contacts integration with rest of Android OS.

- Forwarding messages (digests), from inside the app.

- Full IMAP folders. The app is more "lite", than complete all-features gmail-replacement.

- Ordinary non-SSL/TLS.

- Printing messages on papaer. You can save them to file, and print them manually.

# Permissions

InboxPager uses android permissions on the local device for the following reasons:

ACCESS_NETWORK_STATE, INTERNET:

Communication with user defined message servers. Downloading/Uploading messages.

VIBRATE:

Device can be made to vibrate, if new messages have arrived. Users can disable this setting from inside the application.

WRITE_EXTERNAL_STORAGE:

In order to save messages or attachments on an SDCARD.
IF users save only to internal memory, then the permission can be disabled entirely.

## Requirements

In general - a network connection that does not implement (small) download quotas.

For a POP (Post Office Protocol 3) mail server:

- Support for the extensions TOP, SASL and UIDL.

- LOTS of internal phone memory.

## Known Items

If there are any errors in the application they should be available in the Event Log.

- If while downloading a large attachment you experience errors, then close some other applications to get more RAM.

- Message and attachment sizes should always only an approximation.

- POP has no way to know if a message has been previously seen.

- Sent messages are not saved locally, most servers save those automatically.

## Bug Reporting

https://github.com/itprojects/InboxPager/issues

# GMAIL Configuration

To enable application access to your GMail inbox, go to:

https://www.google.com/settings/security/lesssecureapps

Then and only then, in the application:

Username: user.name@gmail.com

Incoming Mail (IMAP) Server: imap.gmail.com

Port: 993

Outgoing Mail (SMTP) Server: smtp.gmail.com

Port for SSL: 465

Sometimes checking GMAIL too ofter (<10 minutes) may or may not block application access to account.

# OpenPGP Usage

In order to use cryptographic services you need to install an app called OpenKeychain and make, or import, some pgp-keys. OpenKeychain applies OpenPGP privacy/security to a given message,  and the process is described below, or (better) just look at the screenshots. Sending inline messages in non-pgp/mime standard is not supported, but third party apps exist that can do that, through the system clipboard buffer.

IMPORTANT, for BCC messages:

Encrypted blocks may show the recipients' encryption keys' id's. This may leak data, if you're using the blind carbon copy (BCC) message property. For example: a message is encrypted, Alice sends to Bob and Carol; Carol is a BCC, but Carol may also see the key id of Bob.

## Signed Clear Text

Signing a clear, unencrypted message with a pgp key, that will be sent using pgp/mime. This option is for those want to be sure that a message was produced with a certain pgp key, the message contents are not encrypted. Can include attachments.

1. Click the padlock icon, this starts the pgp implementation.

2. Choose "Sign clear text message" spinner.

3. Pick a signing key by pressing on the text button.

4. Ignore recipient keys.

5. Click "START", that produces the pgp/mime.

6. Click "READY", that returns you to the sending activity.

7. Press "SEND".

Some email clients may complain of a "bad signature", i.e. Thunderbird with Enigmail. Manually checking the signature against the firts pgp/mime part with "gpg --verify signature.asc message.txt" is one solution.

## Encrypt Message

Encrypting a message, or signing and encrypting a message. This option is for those that desire more privacy for their content, for example commercial organizations. Messages produced with this option will be encrypted, and they can optionally be signed. [Extra: If one wishes to be able to decrypt their own messages for posterity, use the option to add the signing key to the recipients. Can include attachments.

1. Click the padlock icon, this starts the pgp implementation.

2. Choose "Encrypt" or "Sing and encrypt" from spinner.

3. Pick a signing key by pressing on the text button.

4. Pick the recipient keys by pressing on the text button.

5. Click "START", that produces the pgp/mime.

6. Click "READY", that returns you to the sending activity.

7. Press "SEND".

## Decrypt or Verify Message

Decrypt a pgp/mime message and/or only verifying the signature validity. Can save attachemnts.

1. Click the padlock icon, this starts the pgp implementation.

2. Click "START", that produces the pgp/mime.

3. Click "READY", that returns you to the message activity.

4. Clicking on the icon near the padlock displays signature verification.

5. Clicking on the attachment image button from the top now produces decrypted attachments.

# LICENSES

Application Overall, GPL3

Artwork, CC BY-SA 4.0 License

Font, SIL OPEN FONT LICENSE 1.1

OpenKeychain(Java), Apache 2.0

SQLCipher, Permissive, see file

SQLCipher(Java), Apache 2.0

# Screenshots

<p align="center">
  <img src="https://github.com/itprojects/InboxPager/raw/master/img/2.png" width="250"/>
  <img src="https://github.com/itprojects/InboxPager/raw/master/img/3.png" width="250"/>
  <img src="https://github.com/itprojects/InboxPager/raw/master/img/4.png" width="250"/>
  <img src="https://github.com/itprojects/InboxPager/raw/master/img/5.png" width="250"/>
  <img src="https://github.com/itprojects/InboxPager/raw/master/img/6.png" width="250"/>
  <img src="https://github.com/itprojects/InboxPager/raw/master/img/7.png" width="250"/>
  <img src="https://github.com/itprojects/InboxPager/raw/master/img/8.png" width="250"/>
  <img src="https://github.com/itprojects/InboxPager/raw/master/img/9.png" width="250"/>
  <img src="https://github.com/itprojects/InboxPager/raw/master/img/10.png" width="250"/>
  <img src="https://github.com/itprojects/InboxPager/raw/master/img/11.png" width="250"/>
  <img src="https://github.com/itprojects/InboxPager/raw/master/img/12.png" width="250"/>
  <img src="https://github.com/itprojects/InboxPager/raw/master/img/13.png" width="250"/>
  <img src="https://github.com/itprojects/InboxPager/raw/master/img/14.png" width="250"/>
  <img src="https://github.com/itprojects/InboxPager/raw/master/img/15.png" width="250"/>
  <img src="https://github.com/itprojects/InboxPager/raw/master/img/16.png" width="250"/>
  <img src="https://github.com/itprojects/InboxPager/raw/master/img/cleartext.png" width="250"/>
  <img src="https://github.com/itprojects/InboxPager/raw/master/img/encryption.png" width="250"/>
  <img src="https://github.com/itprojects/InboxPager/raw/master/img/verification.png" width="250"/>
</p>
