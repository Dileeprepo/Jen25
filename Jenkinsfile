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
        sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=simple -Dsonar.host.url=http://13.127.244.224:9000 -Dsonar.login=sqp_e4f5af8d67ed0ee47f161f07cccf5bf2a71a333d'
        
    }

    stage('maven package') {
        sh 'mvn package'
    }
    
    stage('maven deploy') {
        sh 'mvn deploy'
    }




}















   
