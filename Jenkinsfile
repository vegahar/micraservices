pipeline {
    agent none
    options {
        buildDiscarder(logRotator(numToKeepStr: '10'))
    }
    stages {
        stage('Build') {
            agent {
                docker {
                    image 'maven:3-alpine'
                    args '-v /root/.m2:/root/.m2'
                }
            }
            steps {
                sh 'mvn -B -DskipTests clean package'
            }
        }
        stage('Deploy') {
            agent {
                docker {
                    image 'ubuntu:latest'
                }
            }
            steps {
                sh 'cd scripts/ && chmod 755 ./deploy.sh && ./deploy.sh'
            }
        }
    }
}