pipeline{
    agent { label 'GameOfLife-node2' }
    tools{
        jdk 'JDK_8'
    }
    stages{
        stage('Checkout code'){
            steps{
                git url: 'https://github.com/mk2502dev/game-of-life-july23.git'
            }
        }
        stage('Building'){
            steps{
                sh script: 'mvn clean package'
            }
        }
        stage('Archive the artifacts'){
            steps{
                archiveArtifacts artifacts: '**/gameoflife.war'
            }
        }
        stage('JUnit Report'){
                steps{
                    junit testResults: '**/surefire-reports/TEST-*.xml'
                }
        }
    }
    
}