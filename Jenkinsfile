pipeline{
    agent any
    stages{
        stage('checkout'){
            steps{
                checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: '47abb2dd-15e2-4c1d-9348-37cd39fa026d', url: 'https://github.com/n1kkhub/taxi-booking2.git']])
        }
        stage('Build'){
            steps{
                sh "mvn package"
            }
        }
        stage('Deploy to tomcat'){
            steps{
                deploy adapters: [tomcat9(credentialsId: '527db3ea-545b-436b-bcbd-3c786d08d357', path: '', url: 'http://3.137.216.135:8080/')], contextPath: 'goutham', war: '**/*.war'
            }
        }
    }
}
