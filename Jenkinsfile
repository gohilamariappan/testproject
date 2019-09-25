#!groovy
def env = "${env.JOB_BASE_NAME}".split("-").last()

node('anuvaad-dev-swarm') {

try {
   stage('Checkout'){
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
	
	stage('Docker-compose'){
		
		
def src = new File("/home/deploy/workspace/anuvaad/anuvaad-deploy-to-dev/vars/${env}.env")
		
def dest = new File('/home/deploy/workspace/anuvaad/anuvaad-deploy-to-dev/')
dest << src.text

	}
   
 }
catch (err) {
    currentBuild.result = "FAILURE"
    throw err
 }
}
