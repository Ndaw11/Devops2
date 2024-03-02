pipeline {
    agent any
    environment {
        MAVEN_HOME = tool 'maven-3.9.6'
        PATH = "${MAVEN_HOME}/bin:${env.PATH}"
        SCANNER_HOME = tool 'Sonar'
        // Cela peut être Nexus3 ou Nexus2
        NEXUS_VERSION = "nexus3"
        // peut être http ou https
        NEXUS_PROTOCOL = "http"
        //Où est exécuté votre Nexus
        NEXUS_URL = "172.17.0.2:8081"
        // Dépôt où nous téléchargerons l'artefact
        NEXUS_REPOSITORY = "repo_my_job"
        // Identifiant d'identification Jenkins pour s'authentifier auprès de Nexus OSS
        NEXUS_CREDENTIAL_ID = "NEXUS_CRED_JOB"

        ARTIFACT_VERSION = "${BUILD_NUMBER}"
    }
    stages {
        stage('Construction ou Build') {
            steps {
                sh "mvn clean install"
            }
        }
        stage('Test') {
            steps {
                sh "mvn compile"
            }
        }

}
}
}