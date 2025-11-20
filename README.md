pipeline {
    agent any
    tools {
        maven 'MAVEN_HOME'    // Jenkins Maven installation name
    }
    stages {
        stage('git repo & clean') {
            steps {
                // Delete folder if exists
                bat "rmdir /s /q SE_Test || exit 0"
                
                // Clone Git repository
                bat "git clone https://github.com/matetihrushikesh165/SE_Test"
                
                // Clean Maven project
                bat "mvn clean -f SE_Test"
            }
        }
        stage('install') {
            steps {
                // Install dependencies
                bat "mvn install -f SE_Test"
            }
        }
        stage('test') {
            steps {
                // Run unit tests
                bat "mvn test -f SE_Test"
            }
        }
        stage('package') {
            steps {
                // Build the project (JAR/WAR)
                bat "mvn package -f SE_Test"
            }
        }
    }
}
