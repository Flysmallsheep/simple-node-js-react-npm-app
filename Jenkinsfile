pipeline {
    agent {
        //Initialise the Docker inside the Jenkins Server
        docker {
            // Downloads node docker image and runs it as container, Jenkins container and this node container will run locally in the Docker on the VM
            // Then the node container becomes the 'agent' that Jenkins uses to running locally in Docker, but it's short-lived, it will stop once the pipeline is executed
            image 'node:lts-buster-slim'
            //	This args parameter makes the Node container (temporarily) accessible through port 3000, see deliver.sh
            args '-p 3000:3000' 
        }
    }

    environment {
            //environment variable 'CI' is set to true to all steps (i.e. non-interactive mode)
            CI = 'true'
    }

    stages {
        stage('Build') { 
            steps {
                //This sh step executes the npm command to download required dependencies to node_modules directory in Jenkins container
                sh 'npm install' 
            }
        }
        stage('Test') {
              steps {
                sh './jenkins/scripts/test.sh'
              }
        }
        stage('Deliver') {
               steps {
                 sh './jenkins/scripts/deliver.sh'
                 input message: 'Finished using the web site? (Click "Proceed" to continue)'
                 sh './jenkins/scripts/kill.sh'
               }
        }
    }
}
