pipeline {
    agent any
    
    triggers{
        cron(["master", "develop"].contains(BRANCH_NAME) ? "*/3 * * * *" : "")
    }
    
    options {
        buildDiscarder(logRotator(daysToKeepStr: '30'))
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
        stage('Call Slack') {
            steps {
                script {
                    
                    def slack_color = ""
                    if (["SUCCESS", "UNSTABLE"].contains(currentBuild.result)) { slack_color = "good" }
                    if (["FAILURE", "UNSTABLE"].contains(currentBuild.result)) { slack_color = "danger" }

                    def attachments = [
                        [
                            "fallback": "來自 Jenkins CI (OA) 的通知.",
                            "pretext" : "觸發原因 : ${currentBuild.buildCauses.shortDescription}",
                            "color": "$slack_color",
                            "author_name": "Jenkins",
                            "author_link": "$JENKINS_URL",
                            "title": "Job Name : $JOB_NAME",
                            "title_link": "$BUILD_URL",
                            "text": "CI 執行結果為 : $currentBuild.result\nYou can click link to know more details.",
                        ]
                    ]

                    slackSend(attachments: attachments)
                }
            }
        }
    }
}
