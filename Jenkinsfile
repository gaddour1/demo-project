pipeline {
    agent any

    tools {
        maven 'Maven3'
        jdk 'java11'
    }

    stages {
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
            }
        }

        stage('Checkout from SCM') {
            steps {
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/gaddour1/demo-project.git'
            }
        }

        stage('Build with Maven') {
            steps {
                sh 'mvn clean package'   // Use 'bat' if Jenkins agent is Windows
            }
        }

        stage('Run Tests') {
            steps {
                sh 'mvn test'           // Use 'bat' if Windows
            }
        }
    }

    post {
        always {
            echo 'Pipeline finished.'
        }
        success {
            echo 'Build succeeded!'
        }
        failure {
            echo 'Build failed!'
        }
    }
}
