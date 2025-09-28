pipeline
{
    agent {
        label "jenkins-agent"
    }

    tools {
        maven 'Maven3'
        jdk 'java11'
    }

    stages {
        stage('cleanup workspace') {
            steps {
                cleanWs()
            }
        }


} ///
    stages {
        stage('Checkout from scm') {
            steps {
                git branch: 'main', credentialsId: 'github', url: 'https://github.com/gaddour1/demo-project.git'
            }
        }
        
        stage('Build with maven') {
            steps {
                sh 'mvn clean package'
            }
        }

        stage('Run tests') {
            steps {
                sh 'mvn test'
            }
        }


}
}
