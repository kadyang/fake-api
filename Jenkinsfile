pipeline {
    agent any
    triggers{
        cron('*/5 * * * *')
    }

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh 'printenv'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}
