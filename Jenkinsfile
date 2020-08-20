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
                sh "echo $JAVA_HOME"
                sh "/home/ubuntu/neo/tools/neo.sh"
            }
        }
    }
}
