pipeline{
    agent any;
    stages{
        stage("code clone"){
          steps{
              git url : "https://github.com/sha620/node-todo-cicd.git",branch: "master"
          }  
        }
        stage("code build"){
            steps{
               sh "docker build -t new-app:ll ."  
            }
        }
        stage("code test"){
            steps{
                echo "kkk"
            }
            
        }
        stage("push to docker"){
            steps{
                withCredentials([usernamePassword(
                credentialsId: "pok",
                usernameVariable: "user",
                passwordVariable: "pass"
                    )]){
                sh "docker login -u ${env.user} -p ${env.pass}"
                sh "docker image tag new-app:ll ${env.user}/new-app:ll"
                sh "docker push ${env.user}/new-app:ll"
                    }
            }
        }
        stage("code deploy"){
            steps{
                sh "docker run -d new-app:ll"
            }
            
        }
    }
}
