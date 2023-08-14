pipeline{
    agent { label 'GameOfLife-node2' }
    tools{
        jdk 'JDK_8'
        maven 'MAVEN_3.6.3'
    }
    triggers {
        pollSCM('* * * * *')
    }
    stages{
        stage('Checkout code'){
            steps{
                git url: 'https://github.com/mk2502dev/game-of-life-july23.git',
                    branch: 'develop'
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
    post{
        success{
            mail subject: 'Project build successfully!!',
                 body: 'Congratulations your project build successfully without any error',
                 to: 'mbrdi@mercedes-benz.com'
        }
        failure{
            mail subject: 'Build Fails!!',
                 body: 'Sorry your project build failed please see the logs',
                 to: 'mbrdi@mercedes-benz.com'
        }
    }
     
}