pipeline{

    agent any

    environment {
        dockerImage=''
        registry='suryakumarij/demo'
    }

    stages {
        stage('gitclone') {

            steps {
               git branch: 'main', url: 'https://github.com/suryakumari14/dockerproject-1.git'
            }
        }

        stage('Build') {

            steps {
                script{
                    dockerImage = docker.build registry
                }
            }
        }
    }
}  
    
 
