Go to `Datacenter` -> `Notification` 
Then `Notificaton Targets` -> `Add` ->  `SMTP`

Endpoint Name: Gmail
Server: stmp.gmail.com
Encryption: STARTTLS
Port: 587
Username: <email>
Password: <password> created for application

From Address: <email> from Username
Recipient(s): root@pam

Then go to `Permissions` -> `Users` -> `root` and set `E-Mail` with value <email> from Username

Do test on gmail account

Go to `Notification Matcher` -> Targets to notify and switch to Gmail