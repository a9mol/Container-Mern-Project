pipeline {
    agent any
    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/a9mol/Container-Mern-Project.git'
            }
        }
        stage('Build') {
            steps {
                sh 'npm install'
            }
        }
        stage('Test') {
            steps {
                sh 'npm test || echo "No tests yet"'
            }
        }
        stage('Docker Build') {
            steps {
                sh 'docker build -t container-mern-project:latest .'
            }
        }
        stage('Deploy') {
            steps {
                echo "Simulating Deployment..."
                sh 'docker run -d -p 3000:3000 container-mern-project:latest'
            }
        }
    }
}

