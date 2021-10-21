pipeline {
    agent {
        //Initialise the Docker inside the Jenkins Server
        docker {
            // Downloads node docker image and runs it as container, Jenkins container and this node container will running locally in the Docker on the VM
            // Then the node container becomes the 'agent' that Jenkins uses to running locally in Docker, but it's short-lived, it will exit once the pipeline is executed
            image 'node:14-alpine AS builder'
            //	This args parameter makes the Node container (temporarily) accessible through port 3000.
            //  The significance of this is explained in the jenkins/scripts/deliver.sh file
            args '-p 3000:3000' 
        }
    }
    stages {
        stage('Build') { 
            steps {
                //This sh step executes the npm command to download required dependencies to node_modules directory in Jenkins server
                sh 'npm install' 
            }
        }
    }
}
