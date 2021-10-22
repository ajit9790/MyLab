pipeline{
    //Directives
    agent any
    tools {
       maven 'apache-maven'
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
        // stage3 : publish the snapshot over the nexus repository
         stage ('stotre the artifact to Nexus repo '){
            steps {
                nexusArtifactUploader artifacts: [[artifactId: 'AjitDevOpsLab', classifier: '', file: 'target/AjitDevOpsLab-0.0.4-SNAPSHOT.war', type: 'war']], credentialsId: '', groupId: 'com.AjitDevOpsLab', nexusUrl: '172.20.10.128:8081', nexusVersion: 'nexus3', protocol: 'http', repository: 'AjitDevopsLab.SNAPSHOT', version: '0.0.4-SNAPSHOT'
                //withSonarQubeEnv('sonarqube'){ // You can override the credential to be used
                    // sh 'mvn sonar:sonar'
               // }

            }
        }
 
        // Stage4 : Publish the source code to Sonarqube
        stage ('Sonarqube Analysis'){
            steps {
                echo ' Source code published to Sonarqube for SCA......'
                //withSonarQubeEnv('sonarqube'){ // You can override the credential to be used
                    // sh 'mvn sonar:sonar'
               // }

            }
        }

        
        
    }

}