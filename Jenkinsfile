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
    environment {
        JENKINS_BASE_URL      = 'https://jenkins.letgo.cloud'

    }
    options {
        timeout(time: 60, unit: 'MINUTES')
        buildDiscarder(logRotator(numToKeepStr: '10'))
    }
    stages {
        stage('🚢 Configuring K8s tools') {
            steps{
                withCredentials([usernamePassword(credentialsId: 'vault-eks-token', passwordVariable: 'SECRET_ID', usernameVariable: 'ROLE_ID')]) {
                    sh """
			sleep 30
			cat hola.txt
			echo "finish"
                """
                }
            }
        }
    }
}
