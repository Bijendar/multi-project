pipeline {

  agent any

  stages {
     
    stage('code clone') {
        steps {
          echo "This is cloning of code"
          git url: "https://github.com/Bijendar/multi-project.git", branch: "main"      # Git plugin is installed ... (git url: , branch: )  are its operatives \\ 
          echo "Code clone successful!!!"          
        }
    stage('Build') {
         steps{
          echo "This is Building code"
          sh "docker built -t multi-project:latest ."
         } 
        
      
    } 
     stage('Test') {
         echo "This is code testing code"
       
     } 
     stage('Deploy') {
        steps{
          echo "This is Deployment of code"
          sh "docker run -d -p 80:80 multi-project:latest "      
          }
       
       
     } 
     }

    
  }
  
}
