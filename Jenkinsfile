pipeline{
    agent { label 'GameOfLife-node2' }
    tools{
        jdk 'JDK_8'
    }
    stages{
        stage('Checkout code'){
            step{
                git url: 'https://github.com/mk2502dev/game-of-life-july23.git'
            }
        }
        stage('Building')
            step{
                sh script: 'mvn clean package'
            }
    }
    stage('Archive the artifacts'){
            step{
                archiveArtifacts artifacts: '**/gameoflife.war'
            }
    }
    stage('JUnit Report'){
            step{
                junit testResults: '**/surefire-reports/TEST-*.xml'
            }
    }
}