# Presto-Template Connector

This is a [PrestoDB](https://prestodb.io/) connector to query data from [TemplateDB](http://www.templatedb.com/) 

[![Gitter Chat](http://img.shields.io/badge/chat-online-brightgreen.svg)](https://gitter.im/jmrozanec/presto-connectors)
[![Project stats by OpenHub](https://www.openhub.net/p/presto-teradata-connector/widgets/project_thin_badge.gif)](https://www.openhub.net/p/presto-template-connector/)
[![Presto-Connectors Member](https://img.shields.io/badge/presto--connectors-member-green.svg)](http://presto-connectors.ml)

## Development

### How to use this template
You are free to leave everything as is in this template, including the README. Even though, we recommend to

* in the README:
    * replace the word "template", "TemplateDB" for the corresponding database name
    * check badge links: in README template point inexistent links; except for graphics, which direct to existing projects to avoid a broken images.
    * delete "How to use this template" section within the README
* in project files
    * rename package "template" to database name, as well as classes within it
    * delete "mock" package after adding jdbc dependency drivers
    * update the META-INF.services/com.facebook.presto.spi.Plugin file with correct plugin class name

If you have any questions, please contact us at [our Gitter chatroom](https://gitter.im/jmrozanec/presto-connectors)

### Set up
We do not provide TemplateDB JDBC jars, since they require to agree on some terms due to US legislation.
After cloning this repo, you should 

* download TemplateDB JDBC drivers from [here](https://downloads.templatedb.com/download/connectivity/jdbc-driver)
* rename the jars
* place them in the following directories

        $PROJECT_HOME/lib/com/templatedb/config/0.1.0/config-0.1.0.jar
        $PROJECT_HOME/lib/com/templatedb/jdbc/0.1.0/jdbc-0.1.0.jar


### Building the project
To build Presto Template Connector, execute:

    mvn clean install
 

## Installation
### Connection configuration

Create new properties file inside etc/catalog dir:

    connector.name=templatedb
    # connection-url is the TemplateDB JDBC URL. You may use different configurations per environment.
    connection-url=jdbc:templatedb://aaa.bbb.ccc.ddd/TMODE=ANSI,CHARSET=UTF8
	connection-user=someusername
	connection-password=somepassword

To install the connector, copy presto-template-{version}.jar and jars at $PROJECT_HOME/presto-dependencies/ directory to some location, ex.: /tmp/templatedb-jars/

    cd $PRESTODB_HOME
    mkdir -p plugin/templatedb
    cp /tmp/templatedb-jars/* plugin/templatedb
   
   
   
## Known issues and limitations
* [Presto may not support all keywords from some SQL dialects](https://groups.google.com/forum/#!topic/presto-users/tXBuNa19hg8)
* [Presto elaborates its own execution plan before submitting to any DB](https://groups.google.com/forum/#!topic/presto-users/tXBuNa19hg8), which may result in non optimal performance.
 

## Related resources
Below we list resources related to Presto connectors. If you wrote a Presto connector to any database, we want to hear from you!

* [Prestogres: connecting postgres to Presto](http://www.slideshare.net/frsyuki/presto-meetup)

## Contribute & Support!

Contributions are welcome! You can contribute by
 * starring this repo!
 * requesting or adding new features.
 * enhancing existing code or documentation.
 * testing.
 * bringing suggestions and reporting bugs.
 * spreading the word / telling us how you use it!
