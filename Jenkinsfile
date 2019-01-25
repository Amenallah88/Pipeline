 node{
   stage('SCM Checkout'){
     git 'https://github.com/rekikamine/Exemple_Test.git'
   }
   stage('Compile-Package'){
    
    withMaven(jdk: 'java8', maven: 'maven3', tempBinDir: '') {
 
      // Run the maven build
      bat "mvn clean install package"}
     
   }
    stage('publish to Nexus'){
  nexusPublisher nexusInstanceId: 'nexusrep', nexusRepositoryId: 'maven-releases', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: 'target\\testNexus-1.2.jar']], mavenCoordinate: [artifactId: 'nexusartifact', groupId: 'com.hamda', packaging: 'jar', version: '1.7']]]
    } 
 }
