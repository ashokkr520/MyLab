pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
    }
    environment{
       ArtifactId = readMavenPom().getArtifactId()
       Version = readMavenPom().getVersion()
       Name = readMavenPom().getName()
       GroupId = readMavenPom().getGroupId()
    }
    stages {
        // Specify various stage with in stages

        // stage 1. Build
        stage ('Build'){
            steps {
                sh 'mvn clean install package'
            }
        }

        // Stage2 : Testing
        stage ('Test'){
            steps {
                echo ' testing......'

            }
        }

        // Stage3 : Publish the artifacts to Nexus
        stage ('Publish to Nexus'){
            steps {
                nexusArtifactUploader artifacts:
                [[artifactId: 'VinayDevOpsLab',
                classifier: '',
                file: 'target/VinayDevOpsLab-0.0.4-SNAPSHOT.war',
                type: 'war']],
                credentialsId: '70b558b3-9198-4176-aea3-8f027710772d',
                groupId: 'com.vinaysdevopslab',
                nexusUrl: '172.20.10.76:8081',
                nexusVersion: 'nexus3',
                protocol: 'http',
                repository: 'AshokDevOpsLab-SNAPSHOT',
                version: '0.0.4-SNAPSHOT'
                            }
        }

        // Stage 4 : Print some information
        stage ('Print Environment variables'){
                    steps {
                        echo "Artifact ID is '${ArtifactId}'"
                        echo "Version is '${Version}'"
                        echo "GroupID is '${GroupId}'"
                        echo "Name is '${Name}'"
                    }
                }

        // Stage 5 : Deploying the build artifact to Apache Tomcat
        stage ('Deploy'){
            steps {
                echo 'deploying'
            }
        }

    // Stage 6 : Deploying the build artifact to Docker
     




    }

}