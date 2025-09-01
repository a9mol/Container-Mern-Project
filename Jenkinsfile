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
        stage('Docker Build & Push') {
            steps {
                script {
                    docker.withRegistry('https://index.docker.io/v1/', 'dockerhub-pass') {
                        def app = docker.build("1000014838/container-mern-project:latest")
                        app.push()
                    }
                }
            }
        }
        stage('Deploy') {
            steps {
                echo "Simulating Deployment..."
                sh 'docker run -d -p 3000:3000 1000014838/container-mern-project:latest'
            }
        }
    }
}
