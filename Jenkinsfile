pipeline {
    agent { label 'TASK' }
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
    }
}