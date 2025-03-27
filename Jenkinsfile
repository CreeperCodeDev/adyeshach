pipeline {
    agent any
    parameters {
        string(name: 'PORT', defaultValue: '5000', description: 'Forwarded Port')
    }
    stages {
        stage('Pull') {
            steps {
                git 'https://github.com/CreeperCodeDev/adyeshach.git'
            }
        }
        stage('Docker Run') {
            steps {
                sh '''docker rm -f flask-app
                docker build -t simple-flask-app:latest .
                docker run --name flask-app -d -p $PORT:5000 simple-flask-app'''
            }
        }
        stage('Smoke Test') {
            steps {
                sh 'curl localhost:$PORT'
            }
        }
    }
}
