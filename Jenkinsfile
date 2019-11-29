pipeline {
    agent any

    stages {
        stage ('Build') {
            steps {
                sh 'mvn compile'
            }
        }

        stage ('Review') {
            steps {
                sh '-P metrics pmd:pmmd --reportfile target/pmd.xml --exclude vendor/ || exit 0'
                pmd canRunOnFailed: true, pattern: 'target/pmd.xml'
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
