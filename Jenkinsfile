pipeline {
    agent any

    stages {
        stage('checkout code with repository') {
            steps {
                git url: 'https://github.com/mohitkhokhar172/DevOpsClassCodes'
                echo 'checkout done'
            }
        }
        stage('compile the code') {
            steps {
                sh 'mvn compile'
                echo 'compile done'
            }
        }
        stage('test the code') {
            steps {
                sh 'mvn test'
                echo 'testing done'
            }
        }
        stage('qa of code') {
            steps {
                sh 'mvn pmd:pmd'
                echo 'generate report'
                recordIssues sourceCodeRetention: 'LAST_BUILD', tools: [mavenConsole()]
            }
        }
        stage('packaging') {
            steps {
                sh 'mvn package' 
                echo 'convert code'
            }
        }
    }
    post { 
        always { 
            echo 'I will always say Hello again!'
        }
    }
}
