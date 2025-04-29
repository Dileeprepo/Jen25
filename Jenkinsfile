pipeline {
    agent any

    

    stages {
        stage('Code Clone') {
            steps {
                'git branch: 'main', credentialsId: '2abdcd5c-a3e2-4925-ba64-b25fa1e4b732', url: 'https://github.com/Dileeprepo/SP.git''
            }
        }

        stage('Maven Clean') {
            steps {
                sh 'mvn clean'
            }
        }

        stage('Maven Validate') {
            steps {
                sh 'mvn validate'
            }
        }

        stage('Sonar Scan') {
            steps {
                sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=simple -Dsonar.host.url=http://13.232.143.196:9000 -Dsonar.login=sqp_0d8a1b147d177b2dc7ec1d04efead11af6bbdaf5'

                    
            }
        }

        stage('Monitor Project') {
            steps {
                catchError(buildResult: 'SUCCESS', stageResult: 'SUCCESS') {
                
                    sh """
                        chmod +x ./mvnw
                        snyk auth 03767fd1-c4e2-4709-98f7-67ceee7182d6
                        snyk code test
                        snyk test --json --severity-threshold=low
                        snyk monitor --org=Dileeprepo  --project-id=03767fd1-c4e2-4709-98f7-67ceee7182d6  --json > report.json
                    """
                    echo "Snyk monitoring completed successfully."
                }
                
            }
        }
        stage('Maven Compile') {
            steps {
                sh 'mvn compile'
            }
        }

        stage('Maven Test') {
            steps {
                sh 'mvn test'
            }
        }

        

        stage('Maven Package') {
            steps {
                sh 'mvn package'
            }
        }

        stage('Maven Deploy') {
            steps {
                sh 'mvn deploy'
            }
        }
    }
    post {
        success {
            echo 'Pipeline completed successfully.'
        }
        failure {
            echo 'Pipeline failed.'
        }
    }
}














