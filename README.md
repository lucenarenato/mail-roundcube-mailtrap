# Mailtrap Docker Image
<p align="center"><img src="img/install-and-set-up-roundcube-webmail-interface.png"></p>
## Pegar todas as mensagens e exibi-las na interface roundcube.
Catch all mail and display it in roundcube interface.

# Usage

## Start Mailtrap
    $ docker run -d --name=mailtrap -p 1080:80 eaudeweb/mailtrap

    $ docker run -d --name=mailtrap -p 80:80 eaudeweb/mailtrap

## Send email

    $ docker run -it --link mailtrap alpine sh

      $ telnet mailtrap 25
      ehlo example.com
      mail from: me@example.com
      rcpt to: you@example.com
      data
      Subject: Hello from me
      Hello You,

      This is a test.

      Cheers,
      Me
      .
      quit

## See email via Mailtrap Web UI:

* http://localhost

<p align="center"><img src="img/roundcube-webmail-interface.png"></p>

## Default login:

* **Username:** `mailtrap`
* **Password:** `mailtrap`

## Customisations:

Set environment variables

* `MT_USER` - mailbox user, default mailtrap
* `MT_PASSWD` - mailbox user password, default mailtrap
* `MT_MAILBOX_LIMIT` - mailbox limit in bytes, default 51200000
* `MT_MESSAGE_LIMIT` - message limit in bytes, default 10240000

and recreate the container.

## Testing the image locally

```
$ sudo docker build -t eaudeweb/mailtrap:test .
$ sudo docker-compose up
```
- Renato Lucena - 16/10/2019