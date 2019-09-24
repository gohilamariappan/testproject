#!groovy

node('anuvaad-dev-swarm') {

try {
   stage('git Checkout'){
      checkout scm

    }
	
	stage('Docker pull') 
	  withCredentials([string(credentialsId: 'dockerhub_passwd', variable: 'dockerhub_pass')]){
	   
	      sh '''
		  pwd
		  echo $dockerhub_pass > dockerhub_pass.txt
	sudo docker login -u gohila -p "$(cat dockerhub_pass.txt)"
	sudo docker pull gohila/$image_name:$tag_name
	rm dockerhub_pass.txt
	                  
		     '''
		   }
 
   
 }
catch (err) {
    currentBuild.result = "FAILURE"
    throw err
 }
}
