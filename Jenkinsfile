pipeline {
    agent any
    tools {
        maven 'Maven'
    }
    stages {
        stage("build") {
            steps {
                sh 'mvn -v'
            }
        }
        stage("test") {
            steps {
                echo 'Running tests'
            }
        }
        stage("deploy") {
            steps {
                echo 'Deploying application'
            }
        }
        stage("deploy & OWASP Dependency-Check") {
            steps {
                dependencyCheck additionalArguments: '''
                    -o './'
                    -s './'
                    -f 'ALL'
                    --prettyPrint
                ''', odcInstallation: 'TestE3'
                dependencyCheckPublisher pattern: 'dependency-check-report.xml'
            }
        }
    }
}