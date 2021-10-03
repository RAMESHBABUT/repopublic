pipeline {
    agent any

    tools {
        jdk   'myJava'
        maven 'myMaven'
    }

    stages {
        stage('compile') {
            steps {
                git 'https://github.com/RAMESHBABUT/repopublic.git'

                // Run Maven on a Unix agent.
                sh "mvn compile"
            }
        }

        stage('codeReview') {
            steps {
                sh "mvn pmd:pmd"
            }
        }

        stage('unitTest') {
            steps {
                sh "mvn test"
            }
        }

        stage('metricCheck') {
            steps {
                sh "mvn cobertura:cobertura -Dcobertura.report.format=xml"
            }
        }

        stage('package') {
            steps {
                sh "mvn package"
            }
        }



    }
}
