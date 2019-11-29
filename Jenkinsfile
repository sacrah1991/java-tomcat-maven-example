pipeline {
    agent any

    stages {
        stage ('Build') {
            steps {
                sh 'mvn compile'
            }
        }

        
        
        stage ('package'){
            steps {
                echo "Building war file"
                sh 'mvn package'
                archiveArtifacts artifacts : 'target/*.war'
            }
        }

    }
}
