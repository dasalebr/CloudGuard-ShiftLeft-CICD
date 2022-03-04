 pipeline {
      agent any
      environment {
           SECURE_API_TOKEN = credentials("SECURE_API_TOKEN")
           
        }
        
  stages {
          
         stage('Clone Github repository') {
            
    
           steps {
                 
              echo "checking the file"
              
             checkout scm
           
             }
  
          }
          
    stage('Sysdig Secure Scan') {   
       steps {   
                   
         script {      
              try {

             
                
            
                sh 'chmod +x inlinescan_0.2.1_linux_amd64' 

              
           
               } catch (Exception e) {
    
                 echo "Request for Approval"  
                  }
              }
            }
         }
         
     stage('Code approval request') {
     
           steps {
             script {
               def userInput = input(id: 'confirm', message: 'Do you Approve to use this code?', parameters: [ [$class: 'BooleanParameterDefinition', defaultValue: false, description: 'Approve Code to Proceed', name: 'approve'] ])
              }
            }
          }
           
           
          stage('webapp Docker image Build and scan prep') {
             
            steps {

              sh 'docker build -t dhouari/webapp .'
              sh 'docker save dhouari/webapp -o webapp.tar'
              
             } 
           }
        
           
       stage('Sysdig Scanning Container Image Scan') {    
           
            steps {
                script {      
              try {
         
                    sh 'SECURE_API_TOKEN=$SECURE_API_TOKEN ./inlinescan_0.1.2_linux_amd64 --apiurl https://us2.app.sysdig.com'
                   } catch (Exception e) {
    
                 echo "Request for Approval"  
                  }
                }  
             }
          }
            
       stage('Container image approval request') {
     
           steps {
             script {
               def userInput = input(id: 'confirm', message: 'Do you Approve to use this container image?', parameters: [ [$class: 'BooleanParameterDefinition', defaultValue: false, description: 'Approve docker image to Proceed', name: 'approve'] ])
              }
            }
          }
        

                    
              }
            }
  
}
