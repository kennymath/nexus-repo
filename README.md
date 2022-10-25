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
			        nexus-data: {} {}

