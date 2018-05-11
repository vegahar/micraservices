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
                script './scripts/deploy.sh'
            }
        }
    }
}