## setup

Using docker image https://hub.docker.com/r/alexeiled/docker-oracle-xe-11g/

    docker pull alexeiled/docker-oracle-xe-11g
    docker run -d \
    	-v ./sql:/etc/entrypoint-initdb.d \
    	--shm-size=2g \
    	-p 1521:1521 \
    	-p 8080:8080 \
    	alexeiled/docker-oracle-xe-11g

## use new oracle dialect

	curl -L -o server/exp/webapp/WEB-INF/lib/rundeck-oracle-dialect.jar https://github.com/jquick/rundeck_oracle_dialect/blob/master/rundeck-oracle-dialect.jar?raw=true

## rundeck config

~~~ {.properties}
dataSource.url = jdbc:oracle:thin:@localhost:1521:xe
dataSource.driverClassName = oracle.jdbc.driver.OracleDriver
dataSource.username = rundeck
dataSource.password = RUNDECK_PASS
dataSource.dialect = com.rundeck.hibernate.RundeckOracleDialect
dataSource.pooled=true
hibernate.jdbc.use_get_generated_keys=true
~~~