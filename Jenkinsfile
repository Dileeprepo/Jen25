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

    stage('maven package') {
        sh 'mvn package'
    }
}   
