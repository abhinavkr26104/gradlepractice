pipeline {
    agent any
    
    tools {
        // Standard capitalization for Jenkins Global Tool Configuration
        gradle 'Gradle'
        jdk 'JDK'
    }

    stages {
        stage('Checkout') {
            steps {
                // This command tells Jenkins to use the SCM configuration 
                // defined in the Jenkins Job UI (GitHub/GitLab/Bitbucket).
                checkout scm
            }
        }

        stage('Build') {
            steps {
                // Using the Gradle wrapper (./gradlew) is safer for Jenkins 
                // but 'gradle' works if configured in Tools.
                sh 'gradle build'
            }
        }

        stage('Test') {
            steps {
                sh 'gradle test'
            }
        }

        stage('Run Application') {
            steps {
                sh 'gradle display'
            }
        }
    }

    post {
        success {
            echo 'Build and deployment successful'
        }
        failure {
            echo 'Build Failed'
        }
    }
}
