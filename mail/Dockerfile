FROM ubuntu:latest

RUN apt update

RUN apt upgrade -y

RUN apt install postfix dovecot-imapd dovecot-pop3d vim dnsutils iputils-ping telnet -y lsof -y

COPY main.cf /etc/postfix

COPY ./dovecot/* /etc/dovecot/conf.d

COPY start_email.sh /etc/init.d

RUN chmod 755 /etc/init.d/start_email.sh

# PORTAS
EXPOSE 25/tcp 587/tcp 110/tcp 143/tcp 993/tcp 995/tcp

CMD ["/etc/init.d/start_email.sh"]

#start teh postfix Service
#CMD ["/usr/sbin/postfix", "start-fg"]