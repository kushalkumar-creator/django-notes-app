@Library("Shared") _
pipeline{
    
    agent { label "vinod" }
    
    stages{
        stage("Hello"){
            steps{
                script{
                    hello()
                }
            }
        }
        stage("Code"){
            steps{
                script{
                clone("https://github.com/kushalkumar-creator/django-notes-app.git","main")
                }
            }
        }
        stage("Build"){
            steps{
                script{
                     docker_build("notes-app","latest","wratx")
                }
            }
        }
        stage("Push To DockerHub"){
            steps{
                script{
                    docker_push("notes-app","latest","wratx")
                }
            }
        }
        stage("Deploy"){
            steps{
                echo "This is deploying the Code"
                sh "docker compose down && docker compose up -d"
            }
        }
    }
}
