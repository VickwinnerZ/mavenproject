pipeline {
    agent any

    stages {
        stage('Git Checkout') {
            steps {
                git branch: 'main', url: 'https://github.com/VickwinnerZ/mavenproject.git'
            }
        }
        stage('Test') {
            steps {
                sh 'cd SampleWebApp && mvn test'
            }
        }    
        stage('Build') {
            steps {
                sh 'cd SampleWebApp && mvn package'
            }
        }
        stage('Deploy to Tomcat') {
            steps {
                deploy adapters: [tomcat9(credentialsId: 'devops', path: '', 
                url: 'http://52.201.15.159:8080')], 
                contextPath: 'default', 
                war: '**/*.war'
            }
        }
    }
}