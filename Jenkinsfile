pipeline {
    agent any

    stages {
        stage('Checkout the repository') {
            steps {
                checkout scm
            }
        }

        stage('Restore the project') {
            steps {
                bat 'dotnet restore'
            }
        }

        stage('Build the project') {
            steps {
                bat 'dotnet build'
            }
        }

        stage('Run all tests in parallel') {
            parallel {
                stage('Run test for Project 1') {
                    steps {
                        bat 'dotnet test TestProject1 --verbosity normal'
                    }
                }
                stage('Run test for Project 2') {
                    steps {
                        bat 'dotnet test TestProject2 --verbosity normal'
                    }
                }
                stage('Run test for Project 3') {
                    steps {
                        bat 'dotnet test TestProject3 --verbosity normal'
                    }
                }
            }
        }

    }

    post {
        always {
            echo 'Pipeline completed!'
        }
        success {
            echo 'Pipeline succeeded!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}