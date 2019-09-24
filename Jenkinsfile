#!groovy

node('master') {

try {
   stage('git Checkout'){
      checkout scm

    }
   
 }
catch (err) {
    currentBuild.result = "FAILURE"
    throw err
 }
}
