pipeline {
    agent any

    stages{
        stage('clone from github'){
            steps{
                git branch: 'master', url: 'https://github.com/rashidbekraximov/spring-boot-with-jenkins'
            }
        }
        stage('Build Maven'){
            steps{
                sh "mvn clean install package"
            }
        }
    }
}