pipeline{

    agent any

    environment {
        dockerImage=''
        registry='suryakumarij/demo'
        registryCredential='docker_hub'
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
            stage('Push') {
                steps {
                    script {
                        docker.withRegistry('',registryCredential ){
                        dockerImage.push()
                        }
                    }
                }
            }
    }
}  
    
 
