pipeline {

    agent any

    options {
        buildDiscarder logRotator( 
                    daysToKeepStr: '16', 
                    numToKeepStr: '10'
            )
    }

    stages {
        
        stage('Cleanup Workspace') {
            steps {
                cleanWs()
                sh """
                echo "Cleaned Up Workspace For Project"
                """
            }
        }

        stage('Code Checkout') {
            steps {
                checkout([
                    $class: 'GitSCM', 
                    branches: [[name: '*/main']], 
                    userRemoteConfigs: [[url: 'https://github.com/spring-projects/spring-petclinic.git']]
                ])
            }
        }

        stage(' Unit Testing') {
            steps {
                sh """
                echo "Running Unit Tests"
                """
            }
        }

        stage('Code Analysis') {
            steps {
                sh """
                echo "Running Code Analysis"
                """
            }
        }

        stage('Code Analysis 2') {
            steps {
                sh """
                echo "Running Code Analysis"
                sleep 10
                """
            }
        }

        stage('Securtiy Code Analysis') {
            steps {
                sh """
                echo "running security code check"
                sleep 10 
                """
            }
        }

        stage('Build Deploy Code') {
            when {
                branch 'feature'
            }
            steps {
                sh """
                echo "Building Artifact"
                sleep 5
                """

                sh """
                echo "Deploying Code"
                sleep 5
                """
            }
        }

    }   
}
