pipeline {
    agent any

    stages {
        stage ('Compile the code') {
            steps {
                withMaven(maven : 'maven_3_6_3') {
                    sh 'mvn clean compile'
                }
            }
        }

        stage ('Run the tests') {
            steps {
                withMaven(maven : 'maven_3_6_3') {
                    sh 'mvn test'
                }
            }
        }


        stage ('Package the project as a runnable docker image') {
            steps {
                withMaven(maven : 'maven_3_6_3') {
                    sh 'mvn compile jib:dockerBuild'
                }
            }
        }
    }
}
