pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                echo 'Running build automation'
                sh './gradlew build --no-daemon'
                archiveArtifacts artifacts: 'dist/trainSchedule.zip'
            }
        }
         stage('Test') {
            steps {
                echo 'Running test'
            }
        }
        stage('Deploy to Dev Env') {
            steps {
                echo 'Deploying to Dev Env'
            }
        }
        stage('Deploy to QA Env') {
            steps {
                input 'Does the Dev Environment look OK?'
                milestone(1)
                echo 'Deploying to QA Env'
            }
        }
        stage('Deploy to Stage Env') {
            steps {
                input 'Does the QA Environment look OK?'
                milestone(1)
                echo 'Deploying to Stage Env'
            }
        }
        stage('Deploy to Prod Env') {
            steps {
                input 'Does the Stage Environment look OK?'
                milestone(1)
                echo 'Deploying to Prod Env'
            }
        }
    }
}
