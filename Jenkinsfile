pipeline {
    agent any

    tools {
        maven 'Maven'
        gradle 'Gradle'
        jdk 'JDK'
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/YashwanthK18/maven-to-gradle.git'
            }
        }

        // OPTIONAL: only if you still want Maven build
        stage('Build with Maven') {
            steps {
                sh 'mvn clean install'
            }
        }

        // Build using Gradle
        stage('Build with Gradle') {
            steps {
                sh 'gradle clean build'
            }
        }

        // Run Tests
        stage('Test') {
            steps {
                sh 'gradle test'
            }
        }

        // Run Application (now it will work ✅)
        stage('Run Application') {
            steps {
                sh 'gradle run'
            }
        }
    }

    post {
        success {
            echo 'Pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
