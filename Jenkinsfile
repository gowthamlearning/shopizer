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
                    url:'https://github.com/GOWTHI143/shopizer.git'
            }
        }
        stage('build') {
            steps{
                sh mvn "${params.MVN_GOAL}"
                }
        }
    }
}