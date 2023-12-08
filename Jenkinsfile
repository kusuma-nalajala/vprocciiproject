pipeline{
    agent any
    tools {
        maven "MAVEN3"
        jdk "OracleJDK8"
    }

    environment {
         SNAP_REPO = 'vprofile-snapshot'
         NEXUS_USER = 'admin'
         NEXUS_PASS = 'admin123'
         RELEASE_REPO = 'vprofile-release'
         CENTRAL_REPO = 'vpro-maven-central'
         NEXUSIP = '172.31.89.24'
         NEXUSPORT = '8081'
         NEXUS_GRP_REPO = 'vpro-maven-group'
         NEXUS_LOGIN = 'nexuslogin' 
         
    }

    stages {
        stage('Build') {
            steps {
               sh 'mvn clean install -U -DskipTests -Dmaven.repo.local=~/.m2/repository'
            }
        post {
                success {
                    echo 'Now Archiving...'
                    archiveArtifacts artifacts: '**/target/*.war'
                }
            }
        }

            stage('UNIT TEST'){
            steps {
                sh 'mvn clean install -U -DskipTests -Dmaven.repo.local=~/.m2/repository test'
            }
        }    

		
        
    }           
}

}
}