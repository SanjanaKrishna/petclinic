@Library('my-shared-library@main') _  // Correct syntax

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
                pipeline.checkoutCode()
            }
        }

        stage('Set up Java 17') {
            steps {
                pipeline.setupJava()
            }
        }

        stage('Set up Maven') {
            steps {
                pipeline.setupMaven()
            }
        }

        stage('Build with Maven') {
            steps {
                pipeline.buildProject()
            }
        }

        stage('Upload Artifact') {
            steps {
                pipeline.uploadArtifact('target/bus-booking-app-1.0-SNAPSHOT.jar')
            }
        }

        stage('Run Application') {
            steps {
                pipeline.runApplication()
            }
        }

        stage('Validate App is Running') {
            steps {
                pipeline.validateApp()
            }
        }

        stage('Gracefully Stop Spring Boot App') {
            steps {
                pipeline.stopApplication()
            }
        }
    }

    post {
        always {
            cleanup()
        }
    }
}
