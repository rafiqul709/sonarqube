# sonarqube
sonarqube, sonar-scanner, docker, Linux

##### app.dockerfile

      FROM sonarqube:latest
      
##### docker-compose.yml

```
version: '3'
services:
  sonarqube-test:
    build:
      context: ./
      dockerfile: app.dockerfile
    container_name: sonarqube-test
    environment:
      SONAR_ES_BOOTSTRAP_CHECKS_DISABLE: SONAR_ES_BOOTSTRAP_CHECKS_DISABLE=true
    ports:
      - '9000:9000'
    volumes:
      - sonarqube_data:/opt/sonarqube/data
      - sonarqube_extensions:/opt/sonarqube/extensions
      - sonarqube_logs:/opt/sonarqube/logs
      - sonarqube_temp:/opt/sonarqube/temp

networks:
  sonarnet:
    driver: bridge

volumes:
  sonarqube_data:
  sonarqube_extensions:
  sonarqube_logs:
  sonarqube_temp:
  ```
##### Install sonar-scanner
      download from https://docs.sonarqube.org/latest/analysis/scan/sonarscanner/
      sudo nano ~/.profile
      export PATH=$PATH:/home/rafiq/sonarqube-test/sonar-scanner-cli-4.5.0.2216-linux/sonar-scanner-4.5.0.2216-linux/bin
      export PATH
      
      Then Logout OR restart PC
      
##### Test:

      Brouse http://locahost:9000
      
