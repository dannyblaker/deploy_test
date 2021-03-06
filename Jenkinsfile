pipeline {

    agent any

    stages {

        stage('Build') {
            steps {
                echo 'Building..'
            }
        }

        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }

        stage('Deploy to staging') {
            when {
                branch 'staging'
                expression {
                    currentBuild.result == null || currentBuild.result == 'SUCCESS'
                }
            }
            steps {
                echo 'Deploying to staging..'
            }
        }

        stage('Deploy to production') {
            when {
                branch 'production'
                expression {
                    currentBuild.result == null || currentBuild.result == 'SUCCESS'
                }
            }
            steps {
                echo 'Deploying to production..'
            }
        }
    }

    post {
        always {
            echo 'This will always run'
        }
        success {
            echo 'This will run only if successful'
        }
        failure {
            echo 'This will run only if failed'
        }
        unstable {
            echo 'This will run only if the run was marked as unstable'
        }
        changed {
            echo 'This will run only if the state of the Pipeline has changed'
            echo 'For example, if the Pipeline was previously failing but is now successful'
        }
    }
}