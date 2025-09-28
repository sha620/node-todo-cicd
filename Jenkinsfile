pipeline{
    agent any;
    stages{
        stage("clone"){
            steps{
                git url: "https://github.com/sha620/node-todo-cicd.git", branch:"master"
            }
        }
        stage("build"){
            steps{
                sh "docker build -t nodo-app:ll ."
            }
        }
        stage("test"){
            steps{
                echo "pppp"
            }
        }
        stage("push"){
            steps{
                withCredentials([usernamePassword(
                 credentialsId: "pkk",
                 usernameVariable: "user",
                 passwordVariable:"pass"
                 )]){
                     sh "docker login -u ${env.user} -p ${env.pass}"
                     sh "docker image tag nodo-app:ll ${env.user}/nodo-app:ll"
                     sh " docker push ${env.user}/nodo-app:ll"
                 }
            }
        }
        stage("deploy"){
            steps{
                sh "docker compose up -d"
            }
        }
    }
}
