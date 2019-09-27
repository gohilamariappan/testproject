#!groovy

node('anuvaad-dev-swarm') {

try {
   stage('Checkout'){
      checkout scm
	    }
	
		
	stage('Docker-compose'){
		sh '''
		environment=$(echo "$JOB_BASE_NAME" | rev | cut -d'-' -f 1 | rev)
                echo "$environment"
		cp -rpf ./vars/$environment.env ./$environment.env;
		
		sudo env image="$image_name" tag="$tag_name" docker stack deploy --compose-file=${image_name}.yml gateway
		
		'''

	}
   
 }
catch (err) {
    currentBuild.result = "FAILURE"
    throw err
 }
}
