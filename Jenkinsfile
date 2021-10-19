pipeline {
    agent {
        //Initialise the Docker inside the Jenkins Server
        docker {
            image 'node:lts-buster-slim'
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
