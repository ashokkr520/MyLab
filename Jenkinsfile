pipeline{
    //Directives
    agent any
    tools {
        maven 'maven'
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
        

        //Publish the Artifcat to Nexus
        stage ('Publish to Nexus'){
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'VinayDevOpsLab', classifier: '', file: 'target/VinayDevOpsLab-0.0.4-SNAPSHOT.war', type: 'war']], credentialsId: '24b179aa-640b-4e86-a958-c4b4e51c80e9', groupId: 'com.vinaysdevopslab', nexusUrl: '172.20.10.161:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'AshokDevOpsLab-SNAPSHOT', version: '0.0.4-SNAPSHOT'
            }
        }


        // Stage3: Deploying 
        stage ('Deploy'){
            steps {
                echo 'deploying.....'
            }
            
        }

      
        
    }

}
