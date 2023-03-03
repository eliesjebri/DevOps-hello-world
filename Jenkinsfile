pipeline {
    agent {
        docker {
            image 'maven:3.9.0-eclipse-temurin-11'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
	stage('Clone repository') { 
            steps { 
                script{
                checkout scm
                }
            }
        }
        stage('Build') {
            steps {
                sh 'mvn -B clean install'
            }
        }
        stage('Test') { 
            steps {
		sh 'set -xe'
                sh 'echo mvn -B clean test' 
		sh 'pwd'
            }
        }
	
    }
}
