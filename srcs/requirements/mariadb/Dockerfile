FROM	debian:bullseye

EXPOSE	3306

COPY	tools/init.sh /bin/

RUN		apt-get update -y && \
		apt-get install -y --no-install-recommends --no-install-suggests \
		mariadb-server \
		tini && \
		rm -rf /var/lib/apt/lists/* && \
		chmod +x /bin/init.sh

COPY	conf/50-server.cnf /etc/mysql/mariadb.conf.d/

ENTRYPOINT ["/usr/bin/tini", "--"]
CMD ["/bin/init.sh"]
