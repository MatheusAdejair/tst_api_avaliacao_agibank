pipeline {
    agent any
    stages {
        stage("Code Checkout") {
            steps {
                git branch: "master",
                url: "https://gitlab.com/Jonathan.F/api-validation.git",
                credentialsId: 'matheus_adejair'
            }
        }
        stage("Build Docker Image") {
            steps {
                sh("docker build -t apivalidation .")
            }
        }
        stage("Start Mongo") {
            steps {
                sh("docker run -d --name mongodb --network host mongo")
            }
        }
        stage("Run API Testing") {
            steps {
                sh("docker run --network host apivalidation gradle cleanTest test")
            }
        }
    }
}