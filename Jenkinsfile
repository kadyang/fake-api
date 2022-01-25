pipeline {
    agent any
    triggers{
        cron(["master", "develop"].contains(BRANCH_NAME) ? "*/3 * * * *" : "")
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
