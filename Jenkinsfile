pipeline {
    agent any
    stages {
        stage("Code Checkout") {
            steps {
                git branch: "master",
                url: "https://github.com/MatheusAdejair/tst_api_avaliacao_agibank/",
                credentialsId: 'matheus_adejair'
            }
        }
        stage("Start Mongo") {
            steps {
                sh("docker run -d --name mongodb --network host mongo")
            }
        }
    }
}