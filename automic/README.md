# Automic Connector
This connector is designed to integrate Camunda with Automic, 
providing seamless communication between the two systems. 
The connector has following main functions:

- **Read Objects:** This function allows users to read objects 
from Automic and retrieve information for further processing 
within Camunda
- **Execute Workflows:** This function enables users to execute 
workloads in Automic directly from Camunda


## How to ? 
For Authentication (applies to all operations):

- Server address (Url and Port)
- Username
- Password
- Client ID

To read objects in Automic, the user should provide the following information:
- Name of the object (required)

To execute the workload in Automic, the user should provide the following information:
- Name of the workload (required)
- Alias
- Queue where the workload should be executed
- Timezone
- Execution option: 'Once' (for a single execution) or 'Recurring' (for a periodic execution)


## Important Note
$\color{red}{\text{When the Automic Server is reachable only with https protocol and has a certificate signed through a CA}}$, it is important to trust that server by:
- Downloading the certificate of that server with following command:
  ```bash
  openssl s_client -showcerts -connect host.com:443 -servername host.com </dev/null | openssl x509 -outform PEM > server_cert.pem

- Uploading to certificate to Java truststore:
  ```bash
  sudo keytool -importcert -alias example_cert -file server_cert.pem -keystore $JAVA_HOME/lib/security/cacerts -storepass changeit

- and Starting Camunda Connector Java application by adding this option:
    ```bash
  JAVA_TOOL_OPTIONS=-Djavax.net.ssl.trustStore=PATH_TO_FILE -Djavax.net.ssl.trustStorePassword=PASSWORD


### Support
For any questions or issues regarding the Camunda Automic Connector, 
please reach out to our support team at [camunda-dev@best-blu.de](mailto:camunda-dev@best-blu.de)
