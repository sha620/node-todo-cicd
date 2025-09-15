pipeline{
    agent any;
    stages{
        stage("cloen"){
            steps{
                git url: "https://github.com/sha620/node-todo-cicd.git",branch:"master"
            }
            
        }
        stage("build"){
            steps{
                sh "docker build -t todo-app:ll ."
            }
        }
        stage("test"){
            steps{
                echo "test"
            }
            
        }
        stage("push"){
            steps{
                withCredentials([usernamePassword(
                credentialsId:"lion",
                usernameVariable:"user",
                passwordVariable:"pass"
                    )]){
                        sh "docker login -u ${env.user} -p ${env.pass}"
                        sh "docker image tag todo-app:ll ${env.user}/todo-app:ll"
                        sh "docker push ${env.user}/todo-app:ll"
                        
                    }
                    
                    
            }
            
        }
        stage("deply"){
            steps{
                sh "docker compose up -d"
            }
            
        }
    }
}
