pipeline {
    agent any
    tools{
  maven 'M2_HOME'
  }
    stages {
        stage('GITHUB') {
            steps {
                // Check out the code from the Git repository
               checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[credentialsId: '403f2e27-5017-40c8-be66-4d4cd0b888b6', url: 'https://github.com/SurekhaAinaparthi/Nexus.git']])
            }
        }
        stage('Build') {
            steps {
                // Build the Maven project
                sh 'mvn clean install'
            }
        }
        stage('Unit Tests') {
            steps {
                // Run unit tests, if applicable
                sh 'mvn test'
            }
        }
    }
    post {
        success {
            // Actions to be taken if the pipeline is successful
            echo 'Build and deployment successful!'
        }
        failure {
            // Actions to be taken if the pipeline fails
            echo 'Build or deployment failed!'
            // You might want to send notifications or take other corrective actions here
        }
    }
}

