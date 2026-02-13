pipeline{
    agent any
      triggers {
        githubPush()
    }
    stages{
        stage('Clone repo'){
            steps{
                git branch: 'main', url: 'https://github.com/kingpin1374/DevOps-Project-Two-Tier-Flask-App.git'
                credentialsId: 'github'
            }
        }
        stage('Build image'){
            steps{
                sh 'docker build -t flask-app .'
            }
        }
        stage('Deploy with docker compose'){
            steps{
                // existing container if they are running
                sh 'docker compose down || true'
                // start app, rebuilding flask image
                sh 'docker compose up -d --build'
            }
        }
    }
}
