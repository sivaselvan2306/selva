pipeline {
    agent any
    stages {
        stage ('npm package') {
            steps {
                script {
                    sh 'npm install'
                }
            }
        }
        stage ('docker build') {
            steps {
                script {
                    sh 'docker build -t nodejsapp .'
                }
            }
        }
        stage ('container run') {
            steps {
                script {
                    sh 'docker run -itd --name nodejscont1 -p "8085:8080" nodejsapp'
                }
            }
        }
        stage ('push images to nexus') {
            steps {
                script {
                    sh "docker login -u admin -p Admin 52.195.220.107:9090"
                    sh "docker tag nodejsapp:latest 52.195.220.107:9090/nodejsapp:1.0.0"
                    sh 'docker push 52.195.220.107:9090/nodejsapp:1.0.0'
                }
            }
        }
    }
}
