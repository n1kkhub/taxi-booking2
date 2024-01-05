pipeline {
    agent any
    stages{
        stage('checkout'){
            steps{
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '47abb2dd-15e2-4c1d-9348-37cd39fa026d', url: 'https://github.com/n1kkhub/taxi-booking2.git']])
            }
        }    
        stage('validate'){
            steps{
                sh 'mvn validate'
            }
        }    
        stage('compile'){
            steps {
                sh 'mvn compile'
            }
        }
        stage('test'){
            steps{
                sh 'mvn test'
            }
        }
        stage('package'){
            steps{
                sh 'mvn package'
            }        
        stage('Deploy to tomcat'){
            steps{
                deploy adapters: [tomcat9(credentialsId: 'tomcat', path: '', url: 'http://54.224.102.148:8080/')], contextPath: 'taxi', war: '**/*.war'
            }
        }
    }
}
     