pipeline {
    agent any
    tools{
        maven 'maven_3_9_2'
    }
    stages{
        stage('clone from github'){
            steps{
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/rashidbekraximov/spring-boot-with-jenkins']])
                ssh 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    ssh 'docker build -t spring-boot-with-jenkins .'
                }
            }
        }
        stage('Push to Docker Hub'){
            steps{
                script{
                    ssh 'docker login -u rashidbek -p hashcode8864'
                    ssh 'docker tag spring-boot-with-jenkins rashidbek/spring-boot-with-jenkins:latest'
                    ssh 'docker push rashidbek/spring-boot-with-jenkins:latest'
                }
            }
        }
    }

}
