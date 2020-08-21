pipeline {
    agent any
    stages {
        stage('Build') { 
          steps {
                sh "mvn -version"
                sh "mvn clean install"
            }
        }
        stage('Push') { 
          steps {
                sh "cp /var/lib/jenkins/workspace/sap-maven/target/java-tomcat-maven-example.war  /var/lib/tomcat8/webapps/"
            }
        }
        stage('Neo') { 
          steps {
                sh "/home/ubuntu/neo/tools/neo.sh  list-runtimes -h https://hanatrial.ondemand.com -a p2002559018trial -u P2002559018 -p aravind@SAP7717 "
            }
        }
        stage('Neo Delete') { 
          steps {
               
                sh "/home/ubuntu/neo/tools/neo.sh  delete  --host https://hanatrial.ondemand.com --account  p2002559018trial --user P2002559018 -p aravind@SAP7717 --application firstapp"
          }
        }
         stage('Neo Deploy') { 
          steps {
                sh "/home/ubuntu/neo/tools/neo.sh  deploy  --host https://hanatrial.ondemand.com --account  p2002559018trial --user P2002559018 -p aravind@SAP7717 --application firstapp --source  /var/lib/jenkins/workspace/sap-maven/target/java-tomcat-maven-example.war "
                sh "/home/ubuntu/neo/tools/neo.sh  start  --host https://hanatrial.ondemand.com --account  p2002559018trial --user P2002559018 -p aravind@SAP7717 --application firstapp"
          }
        }
    }
}
