pipeline {
    agent any
 
    triggers {
        // Poll GitHub every ~2 minutes for new commits (no webhook needed)
        pollSCM('H/2 * * * *')
    }
 
    stages {
 
        stage('Build') {
            steps {
                echo '===== Stage 1: Build ====='
                echo 'Task : Compile the source code and package it into a deployable artifact (e.g. a .jar/.war).'
                echo 'Tool : Maven  ->  mvn clean package'
            }
        }
 
        stage('Unit and Integration Tests') {
            steps {
                echo '===== Stage 2: Unit and Integration Tests ====='
                echo 'Task : Run unit tests (verify individual functions) and integration tests (verify components work together).'
                echo 'Tools: JUnit (unit tests) and REST Assured / Selenium (integration tests)'
            }
        }
 
        stage('Code Analysis') {
            steps {
                echo '===== Stage 3: Code Analysis ====='
                echo 'Task : Analyse the code for bugs, code smells and maintainability against industry coding standards.'
                echo 'Tool : SonarQube / SonarCloud'
            }
        }
 
        stage('Security Scan') {
            steps {
                echo '===== Stage 4: Security Scan ====='
                echo 'Task : Scan source code and dependencies for known vulnerabilities (SAST + dependency scanning).'
                echo 'Tool : OWASP Dependency-Check / Snyk'
            }
        }
 
        stage('Deploy to Staging') {
            steps {
                echo '===== Stage 5: Deploy to Staging ====='
                echo 'Task : Deploy the packaged application to a staging server that mirrors production.'
                echo 'Tool : AWS EC2 (via SSH / AWS CLI) or Ansible'
            }
        }
 
        stage('Integration Tests on Staging') {
            steps {
                echo '===== Stage 6: Integration Tests on Staging ====='
                echo 'Task : Run end-to-end / integration tests against staging to confirm production-like behaviour.'
                echo 'Tool : Selenium / Postman (Newman)'
            }
        }
 
        stage('Deploy to Production') {
            steps {
                echo '===== Stage 7: Deploy to Production ====='
                echo 'Task : Promote and deploy the validated application to the production server.'
                echo 'Tool : AWS EC2 (via SSH / AWS CLI) or Ansible'
            }
        }
    }
 
    post {
        success { echo 'Pipeline completed successfully.' }
        failure { echo 'Pipeline failed.' }
    }
}
