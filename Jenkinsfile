pipeline {
    agent any

    

    stages {
        stage('Code Clone') {
            steps {
                git branch: 'main',credentialsId: '2abdcd5c-a3e2-4925-ba64-b25fa1e4b732',url: 'https://github.com/Dileeprepo/SP.git'
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
                sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=simple  -Dsonar.host.url=http://3.108.215.87:9000 -Dsonar.login=sqp_5bed43f62bd4f522b958bfe185728dfeb7b25529'
                    
            }
        }

        stage('Monitor Project') {
            steps {
                
                    sh """
                        chmod +x ./mvnw
                        snyk auth 
                        snyk code test
                        snyk test --json --severity-threshold=low
                        snyk monitor --org=  --project-id=  --json > report.json
                    """
                    echo "Snyk monitoring completed successfully."
                
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
}








