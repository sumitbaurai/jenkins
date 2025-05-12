 pipeline {
    agent any
    tools {
        maven "maven 3.9.2"
    }
    stages {
        stage("clean up"){
            steps {
                deleteDir()
            }
        }
        stage("Clone Repo"){
            steps {
                sh "git clone https://github.com/jenkins-docs/simple-java-maven-app.git"
            }
        }
        stage("Build"){
            steps {
                dir("simple-java-maven-app"){
                    sh "mvn clean install"
                }
            }
        }
        stage("Test"){
            steps {
                dir("simple-java-maven-app"){
                    sh "mvn test"
                }
            }
        }
        stage("Build Remote"){
            steps {
                build job: 'bool pipeline', parameters : [[$class: 'BooleanParameterValue', name: 'enableService', value: true ]]
                }
            }
    }
 }