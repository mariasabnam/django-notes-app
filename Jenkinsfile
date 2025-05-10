@Library('maria') _
pipeline {
    agent {label "maria"}
    stages {
        stage("hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage('clone') {
            steps {
                script{
                clone("https://github.com/mariasabnam/django-notes-app.git" ,"main")
                } 
            }
        }
        stage('Build') {
            steps {
                script{
                docker_build("notes-apps","latest","mariasabnam")
                }
            }
        }
        stage('push to dockerhub') {
            steps {
                script{
                    docker_push("notes-apps","latest","mariasabnam")
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'this is for Deploying the code'
                sh "docker compose up -d"
            }
        }
    }
}
