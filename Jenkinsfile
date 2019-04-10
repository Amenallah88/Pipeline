 node{
  stage('SCM Checkout'){
     git 'https://github.com/rekikamine/Exemple_Test.git'
   }
   stage('Compile'){
      bat "mvn clean"}
  
     stage('Install')
      bat "mvn install"}

  stage('Package'){
      bat "mvn package"}
   }

