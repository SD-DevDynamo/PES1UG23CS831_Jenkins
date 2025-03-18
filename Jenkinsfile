pipeline {
    agent any

    stages {
        stage('Clone Repository') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: '*/main']],
                    userRemoteConfigs: [[url: 'https://github.com/SD-DevDynamo/PES1UG23CS831_Jenkins.git']]
                ])
            }
        }

        stage('Build') {
            steps {
                build 'PES1UG23CS831-1'
                sh 'g++ main/main.cpp -o output'
            }
        }

        stage('Test') {
            steps {
                sh './output'
            }
        }

        stage('Deploy') {
            steps {
                echo 'Deploying application...'
            }
        }
    }

    post {
        failure {
            echo 'Pipeline Failed!'
        }
    }
}
