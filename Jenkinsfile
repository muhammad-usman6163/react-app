pipeline {
    agent any

    stages {
        stage('build') {
            steps {
                echo 'This is build stage'
            }
        }
        stage('test') {
            steps {
                echo 'Test stage'
            }
        }
        stage('deploy') {
            steps {
                script {
                    def dockercmd = "docker run -p 3080:3080 -d musman6163/my-repo:v2"
                    sshagent(['ec2-server-key']) {
                        sh "ssh -o StrictHostKeyChecking=no ec2-user@15.168.13.66 ${dockercmd} "
                    }
                }
            }
        }
    }
}
