 node{
   stage('SCM Checkout'){
     git 'https://github.com/rekikamine/Exemple_Test.git'
   }
   stage('Compile-Package'){
    
    withMaven(jdk: 'java8', maven: 'maven3', tempBinDir: '') {
 
      // Run the maven build
      bat "mvn clean install package"}
     
   }
stage('SonarQube analysis code Quality') {
    // requires SonarQube Scanner 2.8+
    def scannerHome = tool 'sonar_Scanner';
    withSonarQubeEnv('sonarQuabe') {
      bat "${scannerHome}/bin/sonar-scanner.bat -e -Dsonar.projectName=qualite2 -Dsonar.projectVersion=1.3 -Dsonar.projectKey=hamda -Dsonar.sources=src/main/java -Dsonar.language=java"
    }
  }
    stage('publish to Nexus'){
  nexusPublisher nexusInstanceId: 'nexusrep', nexusRepositoryId: 'maven-releases', packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: 'target\\testNexus-1.2.jar']], mavenCoordinate: [artifactId: 'nexusartifa', groupId: 'org.xxx', packaging: 'jar', version: '5.8']]]
    } 
  stage('notification'){
  mail bcc: '', body: 'Ok Ok Ok nice', cc: '', from: '', replyTo: '', subject: 'build avec succées', to: 'mohamed.amine.rekik@gmail.com'
  }
 }
