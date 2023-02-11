pipeline{
    agent any

    stages{
        stage('GIT CHECKOUT'){
            steps{
                git branch: 'main', url: 'https://github.com/vansh7071/jenkins-session.git'
            }

        }
        stage('UNIT TEST'){
            steps{
                sh 'mvn test'
            }
        }
    }
}