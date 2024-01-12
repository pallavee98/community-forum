# Community-forum
![cq_blog_perfect_collaboration_stack](https://github.com/Akshaykumar05/community-forum/assets/114390890/fa4260ac-5c68-46f1-98ea-03f868210f7c)

* I'm building an open-source Community platform for Keenable organization, similar to the Discord and Slack but it would be self hosted.
* For that I have selected **Zulip** tool. And now step by step I'll go for the self

## Self-hosting (Steps)
1. Download server
2. Install script
3. Create new organization
4. Connect SMTP service
5. Add Auth methods
6. Mobile push notifications
7. Maintenance
8. Connect

### Steps with details:
1. Download server

```
cd $(mktemp -d)
curl -fLO https://download.zulip.com/server/zulip-server-latest.tar.gz
tar -xf zulip-server-latest.tar.gz
```

* curl: Command-line tool for making HTTP requests.
* -f: Fail silently (i.e., don't show error messages).
* -L: Follow redirects (if the server responds with a redirect, curl will follow it).
* -O: Save the file with the same name as on the remote server.

2. Install script
* Now we’ll install it. This command uses Certbot for automatic SSL and assumes that you are root user.
```
./zulip-server-*/scripts/setup/install --certbot \
    --email=YOUR_EMAIL --hostname=YOUR_HOSTNAME
```
* So for zulip.gis.chat it becomes:
```
./zulip-server-*/scripts/setup/install --certbot \
    --email=my_support_email@my_domain.de --hostname=zulip.gis.chat
```
   
3. Create new organization
  ![Screenshot from 2023-12-29 18-31-37](https://github.com/Akshaykumar05/community-forum/assets/114390890/74371606-fe75-4714-8fd7-ff2e4cddf2a3)

4. Connect SMTP service
  * Outgoing email (SMTP) credentials that Zulip can use to send outgoing emails to users (e.g. email address confirmation emails during the signup process, message notification emails, password reset, etc.).
  * However, people cannot register yet, so let’s connect the SMTP service to Zulip. All you need to do is add the credentials from your SMTP provider.

* Enter them in /etc/zulip/settings.py and the password in /etc/zulip/zulip-secrets.conf.

```
EMAIL_HOST = "smtp-relay.sendinblue.com"
EMAIL_HOST_USER = "your_registration@email.com"
EMAIL_PORT = 587
```

 * Restart the server with command:

```
bash su zulip -c '/home/zulip/deployments/current/scripts/restart-server'
```
* **I got an error here during restarting the server, that was "authentication denied".**
* **Another error was "403 Forbidden" during opening the link of locally hosted server.**
  
5. Add Auth methods
  * Authentication Service facilitates username/password validation using your on-premises Active Directory/LDAP server. Authentication Service is installed as a virtual appliance and communicates with your local directory using LDAP over SSL.
    
6. Mobile push notifications
  * Push notifications are messages that can be sent directly to a user's mobile device. Unlike in-app messages, push notifications can appear on a lock screen or in the top section of a mobile device.

8. Maintenance
9. Connect
  

## Deployment Architecture
![Screenshot from 2023-12-29 00-16-05](https://github.com/Akshaykumar05/community-forum/assets/114390890/fb381617-f709-4a66-a32d-fa36bfc119eb)

### Deployment Components:
1. Nginx
2. Tornado
3. Django
4. PostgreSQL
   
