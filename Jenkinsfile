pipeline {
    agent any
    tools {
        maven 'maven'
    }

    stages {
        stage ('Build') {
            steps {
                sh 'mvn clean install package'
            }
        }

        stage ('Test') {
            steps {
                echo 'testing ...'
            }
        }

         stage ('Publish to Nexus') {
            steps {
                nexusArtifactUploader artifacts: [
                    [artifactId: 'DevOps', classifier: '', file: 'target/EpamDevOpsHW-0.0.4-SNAPSHOT.war', type: 'war']], credentialsId: 'bd22ed79-f353-378b-88dd-718be3f3f35b', groupId: 'com.devopslab', nexusUrl: '172.20.10.155:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'EpamDevOpsHW-SNAPSHOT', version: '0.0.4-SNAPSHOT'
            }
        }

        stage ('Deploy') {
            steps {
                echo 'deploying ...'
            }
        }
    }
}
