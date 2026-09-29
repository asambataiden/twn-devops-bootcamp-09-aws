#!/usr/bin.env groovy

pipeline {   
    agent any
    stages {
        stage("test") {
            steps {
                script {
                    echo "Testing the application..."

                }
            }
        }
        stage("build") {
            steps {
                script {
                    echo "Building the application..."
                }
            }
        }

        stage("deploy") {
            steps {
                script {
                    echo "Deploying the application..."

                    def dockerRunCmd = 'docker run -d -p 3080:3080 -d asambataiden/demo-app:njs-1.0'
                    sshagent('ec2-server-key') {
                        sh "ssh -o StrictHostKeyChecking=no ec2-user@56.228.31.131 ${dockerRunCmd}"
                    }
                }
            }
        }               
    }
} 
