#!groovy

node('master') {

try {
   stage('git Checkout'){
      checkout scm
<<<<<<< HEAD

=======
       checkout scm
>>>>>>> 2674293a3f99d25887335c7b100b13a75c2d5fd8
    }
   
 }
catch (err) {
    currentBuild.result = "FAILURE"
    throw err
 }
}
