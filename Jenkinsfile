pipeline {
    agent any
    tools{
        maven 'maven_3_1_0'
    }
    stages{
        stage('Build Maven'){
            steps{
                checkout([$class: 'GitSCM', branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/rashidbekraximov/spring-boot-with-jenkins']]])
                sh 'mvn clean install'
            }
        }
        stage('Build docker image'){
            steps{
                script{
                    sh 'docker build -t javatechie/spring-boot-jenkins .'
                }
            }
        }
        stage('Push image to Hub'){
            steps{
                script{
                   withCredentials([string(credentialsId: 'dockerhub-pwd', variable: 'dockerhubpwd')]) {
                   sh 'docker login -u javatechie -p ${dockerhubpwd}'

}
                   sh 'docker push javatechie/spring-boot-jenkins'
                }
            }
        }

    }
}