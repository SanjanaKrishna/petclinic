@Library('my-shared-library@main') _

pipeline {
    agent { label 'Node3' }

    environment {
        JAVA_HOME = '/usr/lib/jvm/java-17-openjdk-amd64'
        MAVEN_HOME = '/usr/share/maven'
        PATH = "${JAVA_HOME}/bin:${MAVEN_HOME}/bin:${env.PATH}"
    }

    stages {
        stage('Checkout Code') {
            steps {
                script {
                    checkoutCode()
                }
            }
        }

        stage('Set up Java 17') {
            steps {
                script {
                    setupJava()
                }
            }
        }

        stage('Set up Maven') {
            steps {
                script {
                    setupMaven()
                }
            }
        }

        stage('Build with Maven') {
            steps {
                script {
                    buildProject()
                }
            }
        }

        stage('Upload Artifact') {
            steps {
                script {
                    uploadArtifact('target/bus-booking-app-1.0-SNAPSHOT.jar')
                }
            }
        }

        stage('Run Application') {
            steps {
                script {
                    runApplication()
                }
            }
        }

        stage('Validate App is Running') {
            steps {
                script {
                    validateApp()
                }
            }
        }

        stage('Gracefully Stop Spring Boot App') {
            steps {
                script {
                    stopApplication()
                }
            }
        }
    }

    post {
        always {
            script {
                cleanup()
            }
        }
    }
}
