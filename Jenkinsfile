pipeline {
    agent any

    stages {
       stage('Clone GitHub Repository') {
          steps {
                git branch: 'master',
                    url: 'https://github.com/mrmohammed05/docker-cicd.git'
            }
        }
         stage('Maven Build') {
            steps {
                sh 'mvn clean package'
            }
        }
         stage('Maven Test') {
            steps {
                sh 'mvn test'
            }
        }

        stage('Maven Compile') {
            steps {
                sh 'mvn compile'
            }
        }
          stage('Docker Build') {
            steps {
                sh 'docker build -t cicd-docker:latest .'
            }
        }
        stage('Docker Image Tag') {
            steps {
                sh 'docker tag cicd-docker:latest mrmohammed/cicd-docker:latest'
            }
        }
        stage('Docker Login') {
       steps {
        sh 'docker login -u mrmohammed -p MDHUB@2004'
       }
     }
    stage('Docker Image Push') {
      steps {
        sh 'docker push mrmohammed/cicd-docker:latest'
    }
}

    }
}
