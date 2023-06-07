pipeline {
    agent any
    tools{
        maven 'maven_3_9_2'
    }
    stages{
        stage('clone from github'){
            steps{
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/rashidbekraximov/spring-boot-with-jenkins']])
                bat 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    bat 'docker build -t genius/spring-boot-with-jenkins .'
                }
            }
        }
        stage('Push to Docker Hub'){
            steps{
                script{
                    bat 'docker login -u rashidbek -p hashcode8864'
                    bat 'docker push genius/spring-boot-with-jenkins'
                }
            }
        }
    }

}
