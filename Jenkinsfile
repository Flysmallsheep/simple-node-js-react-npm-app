pipeline {
    agent any
    stages {
//         Initialise the Docker inside the Jenkins Server

        stage('Build') {
            agent {
                    docker {
                        image 'node:14.18.0'
                        //	This args parameter makes the Node container (temporarily) accessible through port 3000.
                        //  The significance of this is explained in the jenkins/scripts/deliver.sh file
                        args '-p 3000:3000'
                    }
            }
            steps {
                //This sh step executes the npm command to download required dependencies to node_modules directory in Jenkins server
                sh 'ls -a' //list hidden file
                sh 'make uninstall'
                sh 'which npm'
                sh 'npm cache clean --force --loglevel=error'
                sh 'chown -R 111:116 "/usr/local/bin/npm"'

//                 sh 'NPM_CONFIG_PREFIX=~/.npm-global'

                sh 'npm install'
            }
        }
    }
}