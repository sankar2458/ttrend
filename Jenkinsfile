pipeline {
    agent {
        node{
            label 'maven-agent'
        }
    }
environment{
    PATH = "/opt/apache-maven-3.9.5/bin:$PATH"
}
    stages {
        stage('build'){
            steps {
                echo '------------------- Build Started -------------'
                sh 'mvn clean deploy -Dmaven.test.skip=true'
                echo '------------------- Build Completed -------------'
            }
        }

        stage('Unit Test') {
            steps{
                echo '------------------- Unit Test Started -------------'
                sh 'mvn surefire-report:report'
                echo '------------------- Unit Test Completed -------------'
            }
        }

        stage('SonarQube Analysis') {
            environment {
                scannerHome = tool 'Siva-SonarScanner'
            }
            steps { 
                echo '------------------- Sonar Started -------------'
                withSonarQubeEnv('SonarQube-Server') { // If you have configured more than one global server connection, you can specify its name
                sh "${scannerHome}/bin/sonar-scanner"
            }
            echo '------------------- Sonar Analysis Completed -------------'
            }
        }
    }
}