pipeline {
    agent {
        node {
            label 'maven'
        }
    }
    environment {
    PATH = "/opt/apache-maven-3.9.5/bin:$PATH"
    }
    stages {
        stage('build') {
            steps {
                sh 'mvn clean deploy'
            }
        }
        stage('SonarQube analysis') {
            environment {
              scannerHome = tool 'sudha-sonarqube-scanner';
            }
            steps{
              withSonarQubeEnv('sudha-sonarqube-server') { // If you have configured more than one global server connection, you can specify its name
               sh "${scannerHome}/sonar-scanner-4.8.1.3023/bin/sonar-scanner"
                }

             }

       }
        
    }
}
