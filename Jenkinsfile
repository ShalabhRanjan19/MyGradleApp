pipeline {
    agent any

    tools {
        gradle 'your-gradle-version-name'
    }

    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        stage('Build') {
            steps {
                sh 'gradle build'
            }
        }
    }
}
