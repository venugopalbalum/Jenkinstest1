import groovy.json.JSulperClassic
pipeline {
    agent any
    options {
    // Only keep the 10 most recent builds
    buildDiscarder(logRotator(numToKeepStr:'10'))
    }

    stages {
        stage ('Prepare') {
            steps {
                checkout([$class: 'GitSCM',
                    branches: [[name: "origin/declarative"]],
                    doGenerateSubmoduleConfigurations: false,
                    extensions: [[$class: 'LocalBranch']],
                    submoduleCfg: [],
                    userRemoteConfigs: [[
                        credentialsId: 'GIT',
                        url: 'https://github.com/venugopalbalum/Jenkinstest1']]])
            }
        }
        stage('Read pipeline.json'){
            steps{
                script{
                    parsedJson = null
                    inputFile = readFile("{$env.Workspace}/pipeline.json")
                    println "Done reading pipeline."
                }
            }
        }

        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}