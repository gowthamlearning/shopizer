pipeline {
    agent { label 'TASK' }
    triggers { pollSCM('* * * * *')}
    parameters {
        choice(name: 'BRANCH', choices: ['master', 'task', 'final'], description: 'build choice')
        string(name: 'MVN_GOAL', defaultValue: 'mvn package', description: 'maven')
    }
    stages{
        stage('vcs'){
            steps {
                git branch: "${params.BRANCH}",
                    url:'https://github.com/gowthamlearning/shopizer.git'
            }
        }
        stage('build') {
            steps{
                sh "${params.MVN_GOAL}"
            }    
        }
        stage('archive'){
            steps{
                archiveArtifacts artifacts: '**/target/*.jar'
            }
        }
        stage('junit'){
            steps{
                junit'**/surefire-reports/*.xml'
            }
        }
    }
}