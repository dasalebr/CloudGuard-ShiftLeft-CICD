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
          
    stage('Shift Code Scan') {   
       steps {   
                   
         script {      
              try {

             
                
            
                sh 'chmod +x shiftleft' 

                sh './shiftleft code-scan -s .'
           
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
        
           
       stage('ShiftLeft Container Image Scan') {    
           
            steps {
                script {      
              try {
         
                    sh './shiftleft image-scan -t 180 -i webapp.tar'
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
}


