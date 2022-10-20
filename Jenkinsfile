pipeline {
    agent any
    triggers { pollSCM('* * * * *')}
    parameters {
        choice(name: 'BRANCH', choices: ['master', 'task'], description: 'build choice')
    }
    stages{
        stage('vcs'){
            steps {
                git branch: "${params.BRANCH}",
                    url:'https://github.com/GOWTHI143/shopizer.git'
            }
        }
        stage('build') {
            steps{
                sh 'mvn package'
                }
        }
        stage('archive'){
            steps{
                archiveArtifacts artifacts: '**/target/*.jar'
            }
        }
        stage('junit-results') {
            steps{
                junit '**/surefire-reports/*.xml'
            }
        }
    }
}