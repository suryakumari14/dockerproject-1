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

        stage('Login') {

            steps {
                sh 'echo $DOCKERHUB_CREDENTIALS_PSW | docker login -u $DOCKERHUB_CREDENTIALS_USR --password-stdin'
            }
        }

        stage('Push') {

            steps {
                sh 'docker push suryakumarij/demo:2.0'
            }
        }
    }

    post {
        always {
            sh 'docker logout'
        }
    }

}
