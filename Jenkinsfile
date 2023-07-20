pipeline {
    agent any
    environment{
       DOCKERHUB_CREDENTIALS= credentials('dockerhub')
    }
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
        stage("built"){
           steps{
             sh "docker build -t vrajs/devops ."
           }
        }
        stage('Login') {
               steps {
                 sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
               }
             }
             stage('Push') {
               steps {
                 sh 'docker push vrajs/devops'
               }
             }
           }
           post {
             always {
               sh 'docker logout'
             }
           }
    }
}