pipeline {
agent any
stages {
stage ('Compile Stage') {
steps {
withMaven(maven : 'maven-3.6.0') {
bat'mvn clean compile'
}
}
}
stage ('Testing Stage') {
steps {
withMaven(maven : 'maven-3.6.0') {
bat'mvn test'
}
}
}
stage ('Install Stage') {
steps {
withMaven(maven : 'maven-3.6.0') {
bat'mvn install'
}
}
}
}
}
