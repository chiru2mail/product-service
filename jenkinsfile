pipeline{
    agent any
    tools{
        maven 'maven_3_9_0'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/chiru2mail/product-service']])
                bat 'mvn clean install'
            }
        }
        stage('Build Docker image'){
            steps{
                script{
                    bat 'docker build -t chiru2mail/product-service:1.0 .'
                }
            }
        }
        stage('Push image to Docker Hub'){
            steps{
                script{
                    bat 'docker login -u chiru2mail -p sairamom123'
                    bat 'docker push chiru2mail/product-service:1.0'
                }
            }
        }
    }
}