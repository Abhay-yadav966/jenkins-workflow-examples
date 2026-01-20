pipeline{
    agent any

    tools{
        jdk 'JDK_21'
    }

    stages{
        stage('Checkout Code'){
            steps{
                checkout scm
            }
        }

        stage('Build'){
            steps{
                sh './gradlew clean build'
            }
        }

        stage('Run Tests'){
            steps{
                sh './gradlew test'
            }
        }

        stage('Archive Artifact'){
            steps{
                archiveArtifacts artifacts: 'build/libs/*.jar', fingerprint: true
            }
        }
    }

    post{
        success{
            echo 'Build Successfully'
        }
        failure{
            echo 'Build Failed'
        }
    }
}