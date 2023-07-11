pipeline {
    agent any
    stages{
        stage("checkout"){
            steps{
                git  url: 'https://github.com/Vimal-Raj-S/Devops_project.git '
            }
        }
        stage("build"){
            steps{
                sh "mvn clean compile "
            }
        }
        stage("test"){
            steps{
                sh "mvn test"
            }
        }
    }
}