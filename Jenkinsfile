pipeline {
    agent any
    tools {
        maven 'maven'
    }

    environment {
        ArtifactId  = readMavenPom().getArtifactId()
        Version     = readMavenPom().getVersion()
        Name        = readMavenPom().getName()
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
                nexusArtifactUploader artifacts: 
                [[artifactId: 'DevOpsLab', 
                classifier: '', 
                file: 'target/DevOpsLab-0.0.4-SNAPSHOT.war', 
                type: 'war']], 
                credentialsId: '51231d5b-eb83-4b91-8e8f-56020908d643', 
                groupId: 'devopslab', 
                nexusUrl: '172.20.10.155:8081', 
                nexusVersion: 'nexus3', 
                protocol: 'http', 
                repository: 'EpamDevOpsHW-SNAPSHOT', 
                version: '0.0.4-SNAPSHOT'
            }
        }

        stage ('Print ENV Variables') {
            steps {
                echo "Artifact ID is '${ArtifactId}'"
                echo "Version is '${Version}'"
                echo "GroupID is '{}'"
                echo "Name is '${Name}'"
            }
        }

        stage ('Deploy') {
            steps {
                echo 'deploying ...'
            }
        }
    }
}
