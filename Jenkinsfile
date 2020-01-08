pipeline {
    agent any //here we can mention slave or master if any then job will run wherever in available master or slave

    stages {
        stage ('Build') {
            steps {
                sh 'mvn compile' //compile command
            }
        }

        stage ('Review') {
            steps {
                sh '-P metrics pmd:pmd --reportfile **/*.xml --exclude vendor/ || exit 0'
                pmd canRunOnFailed: true, pattern: '**/*.xml'
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
