pipeline{

    agent any

    stages{

        stage('Continous Download') {

            steps{
                git branch: 'main', url: 'https://github.com/Hadijah-ateh/PROJECT.git'
            }
        }
        stage("Intergration Testing"){

            steps{
                sh 'mvn verify -DskipUnitTests'
            }
        }
        stage("Unit Testing"){

            steps{
                sh 'mvn test'
            }
        }
        stage("Continous Build"){

            steps{
                sh 'mvn clean install'
            }
        }
        stage("Static Test Analysis"){

            steps{

                scrip{
                    withSonarQubeEnv(credentialsId: 'sonarqube-token'){
                        sh 'mvn clean package sonar:sonar'
                    }
                }
            }
        }
    }
}