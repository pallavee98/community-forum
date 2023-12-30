# Community-forum
* I'm building an open-source communication platform similar to Discord and Slack but it will be self hosted.
* For that I have selected **Zulip** tool.

## Self-hosting
* Download server
* Install script
* Create new organization
  ![Screenshot from 2023-12-29 18-31-37](https://github.com/Akshaykumar05/community-forum/assets/114390890/74371606-fe75-4714-8fd7-ff2e4cddf2a3)

* Connect SMTP service
  * Outgoing email (SMTP) credentials that Zulip can use to send outgoing emails to users (e.g. email address confirmation emails during the signup process, message notification emails, password reset, etc.).
  * However, people cannot register yet, so let’s connect the SMTP service to Zulip. All you need to do is add the credentials from your SMTP provider.

* Enter them in /etc/zulip/settings.py and the password in /etc/zulip/zulip-secrets.conf.

'''EMAIL_HOST = "smtp-relay.sendinblue.com"
EMAIL_HOST_USER = "your_registration@email.com"
EMAIL_PORT = 587'''

 * Restart the server with

''' su zulip -c '/home/zulip/deployments/current/scripts/restart-server' '''

* Add Auth methods
* Mobile push notifications
* Maintenance
* Connect
  

## Deployment Architecture
![Screenshot from 2023-12-29 00-16-05](https://github.com/Akshaykumar05/community-forum/assets/114390890/fb381617-f709-4a66-a32d-fa36bfc119eb)
