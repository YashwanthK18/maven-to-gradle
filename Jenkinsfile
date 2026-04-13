pipeline {
    agent any

    tools {
        maven 'Maven'     // Name configured in Jenkins
        gradle 'Gradle'   // Name configured in Jenkins
        jdk 'JDK'         // Name configured in Jenkins
    }

    stages {

        stage('Checkout') {
            steps {
                git branch: 'master', url: 'https://github.com/YashwanthK18/maven-to-gradle.git'
            }
        }

        // STEP 1: Build using Maven (before conversion)
        stage('Build with Maven') {
            steps {
                sh 'mvn clean install'
            }
        }

        // STEP 2: Convert Maven → Gradle
        stage('Convert to Gradle') {
            steps {
                sh 'gradle init --type pom'
            }
        }

        // STEP 3: Build using Gradle
        stage('Build with Gradle') {
            steps {
                sh 'gradle build'
            }
        }

        // STEP 4: Run Tests
        stage('Test') {
            steps {
                sh 'gradle test'
            }
        }

        // STEP 5: Run Application (optional)
        stage('Run Application') {
            steps {
                sh 'gradle run'
            }
        }
    }

    post {
        success {
            echo 'Maven to Gradle pipeline executed successfully!'
        }
        failure {
            echo 'Pipeline failed!'
        }
    }
}
