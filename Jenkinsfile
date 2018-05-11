pipeline {
    agent none
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
                sh 'printenv'
            }
        }
        stage('deploy') {
            agent {
                docker {
                    image 'ubuntu:latest'
                }
            }
            steps {
                sh 'ls'
                sh 'pwd'
                sh 'printenv'
                sh 'whoami'
                sh 'echo $HOME'
                sh 'echo $USER'
                bash './scripts/deploy.sh'
            }
        }
    }
}