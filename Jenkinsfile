pipeline {
    
    agent{ 
        label 'agent-1'
    }

    stages {

        stage('Checkout') {
            steps {
                checkout scm
            }
        }

        stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Package') {
            steps {
                sh 'ls -l target/'
            }
        }
    }
    stage('Credentials Test') {
    steps {
        withCredentials([string(credentialsId: 'demo-secret', variable: 'MY_SECRET')]) {
            sh 'echo "Secret loaded successfully"'
        }
    }
}

    post {

        success {
            echo 'Pipeline completed successfully'
        }

        failure {
            echo 'Pipeline failed'
        }

        always {
            echo 'Pipeline finished'
            // Webhook test
            // Webhook test 2
        }
    }
}
