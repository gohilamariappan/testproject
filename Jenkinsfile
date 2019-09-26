#!groovy

node('anuvaad-dev-swarm') {

try {
   stage('Checkout'){
      checkout scm
	    }
	
		
	stage('Docker-compose'){
		sh '''
		environment=$(echo "$JOB_BASE_NAME" | cut -d '-' -f 4)
                echo "$environment"
		cp -rpf ./vars/$environment.env ./dev.env;
		sudo env image="$image_name" tag="$tag_name" docker stack deploy --compose-file=${image_name}.yml anuvaad
		
		'''

	}
   
 }
catch (err) {
    currentBuild.result = "FAILURE"
    throw err
 }
}
