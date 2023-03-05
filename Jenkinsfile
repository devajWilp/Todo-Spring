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
                sh 'mvn clean package'
            }
        }
        stage('Deploy') {
            steps {
                // deploy the WAR file to Tomcat
                // get the Tomcat manager username and password from environment variables
                withCredentials([usernamePassword(credentialsId: 'tomcat-credentials', usernameVariable: 'deployer', passwordVariable: 'password')]) {
                  // deploy the WAR file using the Tomcat manager API
                  sh "curl -v -u $TOMCAT_USERNAME:$TOMCAT_PASSWORD --upload-file target/*.war http://localhost:8080/manager/text/deploy?path=/app&update=true"
                }
        }
    }
}