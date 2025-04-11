node {
    stage('code clone') {
        git branch: 'main', credentialsId: '2abdcd5c-a3e2-4925-ba64-b25fa1e4b732', url: 'https://github.com/Dileeprepo/SP.git'
        
    }

    stage('maven clean') {
        sh 'mvn clean'
    }

    stage('maven validate') {
        sh 'mvn validate'
    }

    stage('maven compile') {
        sh 'mvn compile'
        
    }
    stage('maven test') {
        sh 'mvn test'
        
    }
    stage('sonar scan') {
        sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=simple  -Dsonar.host.url=http://3.108.215.87:9000 -Dsonar.login=sqp_5bed43f62bd4f522b958bfe185728dfeb7b25529'
        
    }

    stage('maven package') {
        sh 'mvn package'
    }
    
    stage('maven deploy') {
        sh 'mvn deploy'
    }
}




















   
