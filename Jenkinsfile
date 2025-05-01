pipeline {
    agent any

    tools {
        jdk 'jdk-17'         // Ensure 'jdk-17' is set in Jenkins > Global Tool Configuration
        gradle 'Gradle'      // Ensure 'Gradle' is configured in the same place
    }

    environment {
        JAVA_HOME = "${tool 'jdk-17'}"
        GRADLE_HOME = "${tool 'Gradle'}"
        PATH = "${JAVA_HOME}/bin:${GRADLE_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout') {
            steps {
                git url: 'https://github.com/ShalabhRanjan19/MyGradleApp.git', branch: 'main'
            }
        }

        stage('Build') {
            steps {
                sh 'gradle clean build'
            }
        }

        stage('Archive JAR') {
            steps {
                archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
            }
        }
    }

    post {
        success {
            echo 'Build and archiving successful!'
        }
        failure {
            echo ' Sorry Build failed!'
        }
    }
}
