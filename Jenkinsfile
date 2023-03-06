pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                // checkout code from git repository
                git 'https://github.com/devajWilp/Todo-Spring'
            }
        }
        stage('Build and Test') {
            steps {
                // build and test the Java Maven application
                bat 'mvn clean install'
            }
        }
        stage('Deploy') {
            steps {
                // deploy the WAR file to Tomcat
                // get the Tomcat manager username and password from environment variables
                // deploy the WAR file using the Tomcat manager API
                bat 'curl -v -u "deployer:password" --upload-file target/todo-0.0.1-SNAPSHOT.war "http://localhost:8080/manager/text/deploy?path=/app&update=true"'
        }
    }
}
}