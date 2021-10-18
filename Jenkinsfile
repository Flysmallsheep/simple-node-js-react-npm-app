pipeline {
    agent {
        //Download a Node docker image and run it as a container (which will build Node.js and React application)
        //This Node container will become the agent that Jenkins uses to run the pipeline project, however, the container is short-lived,
        //- its lifespan is only that of the duration of your Pipeline’s execution.
        docker {
            image 'node:lts-buster-slim'
            //	This args parameter makes the Node container (temporarily) accessible through port 3000.
            //  The significance of this is explained in the jenkins/scripts/deliver.sh file
            args '-p 3000:3000'
        }
    }
    stages {
        //Initialise the Docker inside the Jenkins Server
//         stage('Initialize'){
//             steps {
//                 script {
//                     def dockerHome = tool 'Docker'
//                     env.PATH = "${dockerHome}/bin:${env.PATH}"
//                 }
//             }
//         }
        stage('Build') {
            steps {
                //This sh step executes the npm command to download required dependencies to node_modules directory in Jenkins server
                sh 'ls -a' //list hidden file
                sh 'which npm'
//                 sh 'chattr -i "/usr/local/bin/npm"'
//                 sh 'chown -R 111:116 "/usr/local/bin/npm"'
                sh 'chown -R $(whoami) "/usr/local/bin/npm"'
                sh 'npm install'
            }
        }
    }
}