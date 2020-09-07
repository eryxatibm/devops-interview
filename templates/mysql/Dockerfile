FROM mysql/mysql-server:latest

ADD init_db.sql /docker-entrypoint-initdb.d

EXPOSE 3306

# Must login with a the OTP on first Docker run and then
# update the original password to allow queries
#  E.g:
#   $ docker run exect -ti /bin/bash
#   $ mysql -u root -p <use one time password on prompt>
#   $ ALTER USER 'root'@'localhost' IDENTIFIED BY 'password';