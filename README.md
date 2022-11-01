version: "2"

services:
  nexus:
      image: sonatype/nexus3
          restart: always
	      volumes:
	            - "./nexus:/nexus-data"
		        ports:
			      - "8081:8081"

			      volumes:
			        nexus-data: {} {} {{}}

version: '2'

services:

 sonarqube:
   image: sonarqube:6.3.1
     container_name: sonarqube
       restart: always
         ports:
	    - "9000:9000"
	      environment:
	         - SONARQUBE_JDBC_URL=jdbc:postgresql://sonardb:5432/sonar
		    - SONARQUBE_JDBC_USERNAME=sonar
		       - SONARQUBE_JDBC_PASSWORD=sonar
		         volumes:
			     - "sonarqube_data:/opt/sonarqube/data"
			         - "sonarqube_extensions:/opt/sonarqube/extensions"
				     - "sonarqube_logs:/opt/sonarqube/logs"
				     	
					 sonardb:
					   image: postgres:9.6.1
					     container_name: postgres
					       restart: always
					         environment:
						    - POSTGRES_USER=sonar
						       - POSTGRES_PASSWORD=sonar
						         ports:
							     - "5432:5432"
							       volumes:
							           - "/opt/postgres:/var/lib/postgresql"
								       - "/opt/postgresql_data:/var/lib/postgresql/data"

								       volumes:
								         sonarqube_data:
									   sonarqube_extensions:
									     sonarqube_logs:
									       postgresql:
									         postgresql_data:
