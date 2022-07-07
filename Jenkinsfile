pipeline{

    agent any

    environment {
        DOCKERHUB_CREDENTIALS=credentials('docker_hub')
    }

    stages {
        
        stage('gitclone') {

            steps {
               git branch: 'main', url: 'https://github.com/suryakumari14/dockerproject-1.git'
            }
        }

        stage('Build') {

            steps {
                sh 'docker build -t suryakumarij/demo:2.0 .'
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
