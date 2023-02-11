pipeline{
    agent any

    stages{
        stage('GIT CHECKOUT'){
            steps{
                git branch: 'main', url: 'https://github.com/vansh7071/jenkins-session.git'
            }

        }
        stage('UNIT TESTING'){
            steps{
                sh 'mvn test'
            }
        }
        stage('INTEGRATION TESTING'){
            steps{
                sh 'mvn verify -DskipUnitTests'
            }
        }
    }
}