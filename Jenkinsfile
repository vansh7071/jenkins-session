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
        stage('MAVEN BUILD'){
            steps{
                sh 'mvn clean install'
            }
        }
        stage('STATIC CODE ANALYSIS'){
            steps{
                script{
                    withSonarQubeEnv(credentialsId: 'sonarqube_token') {
                      // some block
                      sh 'mvn clean package sonar:sonar'

                    }
                }
            }
        }
        stage('QUALITY GATE STATUS'){
            steps{
                script{
                    waitForQualityGate abortPipeline: false, credentialsId: 'sonarqube_token'
                }
            }
        }
        stage('Upload Artifacts To Nexus'){
            steps{

                script{

                    nexusArtifactUploader artifacts: [[artifactId: 'springboot', classifier: '', file: 'target/Thapar.jar', type: 'jar']], credentialsId: 'nexus_login', groupId: 'com.example', nexusUrl: '54.90.11.227:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'java-release', version: '1.0.0'
                }
            }
        }
        stage("Docker Image Build"){

            steps {

                script {
                    sh 'docker image build -t $JOB_NAME:v1.$BUILD_ID .'
                    sh 'docker image tag $JOB_NAME:v1.$BUILD_ID vansh7071/$JOB_NAME:v1.$BUILD_ID'
                    sh 'docker image tag $JOB_NAME:v1.$BUILD_ID vansh7071/$JOB_NAME:latest'
                }
            }
        }
    }
}