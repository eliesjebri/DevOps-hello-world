pipeline {
    agent {
        docker {
            image 'maven:3.9.0-eclipse-temurin-11'
            args '-v /root/.m2:/root/.m2'
        }
    }
    stages {
		stage ('cloneSCM') {
			steps {
                		checkout([$class: 'GitSCM', branches: [[name: '*/main']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/eliesjebri/DevOps-hello-world.git']]])
                		sh "ls -lart ./*"
            }
		}
        stage('Build') {
            steps {
                sh 'mvn -B clean install'
            }
        }
        stage('Test') { 
            steps {
                sh 'mvn -B clean test' 
            }
            post {
                always {
                    junit 'target/surefire-reports/*.xml' 
                }
            }
        }
    }
}
