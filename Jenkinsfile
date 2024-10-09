@Library("Shared_Library") _
pipeline {
    agent {label "Node1"}
    stages{
        stage("MSG"){
            steps{
                script{
                    text("Abhishek")
                }
            }
        }
        stage("clone"){
            steps{
                script{
                    git_clone("https://github.com/Abhishek-Kumar-Srivastava03a/django-notes-app.git","main")
                }
            }
        }
        stage("build"){
            steps{
                script{
                    build("django-app","latest")
                }
                
            }
        }
        stage("push to docker hub"){
            steps{
                script{
                    docker_push("DockerCreds","django-app","latest")
                }
            }
        }
        stage("deploy"){
            steps{
                sh "docker compose -f docker-compose.yml down"
                script{
                    deploy("docker-compose.yml")
                }
            }
        }
    }
}
