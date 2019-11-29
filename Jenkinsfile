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
                echo "Archiving artifacts"
                archiveArtifacts artifacts : 'target/*.war'
            }
        }

    }
}
