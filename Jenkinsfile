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
                def tomcatUrl = "http://localhost:8080/manager/text/deploy?path=/app&update=true"
                def warFile = "target\\*.war"
                def authString = "deployer:password"
      
                bat "curl -v -u ${authString} --upload-file ${warFile} ${tomcatUrl}"
        }
    }
}
}