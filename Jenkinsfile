pipeline {
    agent {
        node{
            label 'maven-agent'
        }
    }

    stages {
        stage('Clone Project') {
            steps {
                git branch: 'main', url: 'https://github.com/sankar2458/ttrend.git'
            }
        }
    }
}
