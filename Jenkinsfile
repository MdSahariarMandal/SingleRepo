pipeline {
    agent any
    
    tools  {
        maven 'MAVEN3'
    }
   
    stages {
        stage('Build java project') {
            steps {
                echo 'java project start'
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/MdSahariarMandal/SingleRepo.git']])
                bat 'javac Hello.java'
                bat 'java Hello'
                script{
                    bat 'docker build -t Hello .'
                    bat 'docker tag Hello sahariar007/hello'
                    bat 'docker push sahariar007/hello'
                    bat 'docker pull sahariar007/hello'
                    bat 'docker run sahariar007/hello'
                }

            }
        }
        stage('build python project'){
            steps{
                echo 'python project start '
                bat 'python Hello.py'
                checkout scmGit(branches: [[name: '*/main']], extensions: [], userRemoteConfigs: [[url: 'https://github.com/MdSahariarMandal/SingleRepo.git']])
                script{
                    bat 'docker build -t Hello.py .'
                    bat 'docker tag Hello.py sahariar007/hello'
                    bat 'docker push sahariar007/hello'
                    bat 'docker pull sahariar007/hello'
                }
            }
        }
    }
}
