node('master') {
    // some block
   stage('SCM Checkout'){
     git 'https://github.com/ashok-g/app1.git'
   }
   stage('Compile-Package'){
      // Get maven home path
      def mvnHome =  tool name: 'maven-3', type: 'maven'   
      sh "${mvnHome}/bin/mvn clean package"
   }
    
    
        
     stage('nexus artifact uploader'){
            nexusArtifactUploader artifacts: [[artifactId: '$BUILD_TIMESTAMP',
            classifier: '', file: '/var/lib/jenkins/workspace/Jenkins-Sonarqube-nexus/target/*.war', type: 'war']], 
            credentialsId: 'f3390c6a-2656-4419-a68d-ddc7ebd8a426', groupId: 'dev', nexusUrl: '34.218.209.217:8081/nexus',
            nexusVersion: 'nexus2', protocol: 'http', repository: 'test', version: '$BUILD_ID'

        }
}
