node {
    stage('code clone') {
        git branch: 'main', credentialsId: 'Dileeprepo', url: 'https://github.com/Dileeprepo/demo.git'
        
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
        sh 'mvn clean verify sonar:sonar -Dsonar.projectKey=simple -Dsonar.host.url=http://65.0.75.220:9000 -Dsonar.login=sqp_5e48abdaa0f96b71b8b60904730f78c5b1299a43'
        
    }

    stage('maven package') {
        sh 'mvn package'
    }
    
    stage('maven deploy') {
        sh 'mvn deploy'
    }

}













   
