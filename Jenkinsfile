@Library("Shared") _
pipeline{
    agent {label "jenkinsAgent"}
    stages{
        stage("Hello"){
            steps{
                script{
                   hello()  //Name of the groovy file
                }
            }
        }
        stage("Code"){
          steps{
              script{
               clone("https://github.com/ayushsachan123/django-webhook.git", "main")
            } 
          }
        }
        stage("Build"){
            steps{
                script{
                   docker_build("notes-app", "latest", "ayushsachan123")
                }
            } 
        }
        stage("Push to DockerHub"){
            steps{
               script{
                  docker_push("notes-app", "latest","ayushsachan123")
                } 
              }
            }
        stage("Deploy"){
            steps{
                echo "This is deploying the code"
                // sh "docker run -d -p 8000:8000 notes-app:latest"
                sh "docker compose up -d"
            }
        }
    }
}
