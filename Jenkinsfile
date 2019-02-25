#!groovy


pipeline {
    agent {
        kubernetes {
            label "jenkins-slave"
            yamlFile './jenkinsfiles/agent.yml'
        }
    }
    parameters {
        booleanParam(defaultValue: true, description: 'Deploy this release', name: 'DEPLOY')
    }
    stages {
        stage('Configuring K8s tools') {
            steps{
            	sh "hostname"
            }
        }
    }
}
