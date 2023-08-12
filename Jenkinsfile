pipeline {
    agent any

    environment {
        TOMCAT_WEBAPPS = '/var/lib/tomcat9/webapps' // Set this to the actual path of the Tomcat webapps directory
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the Git repository
                checkout scm
            }
        }

       

        stage('Build HTML') {
            steps {
                script {
                    // Add any necessary build or processing steps for HTML files here
                    // For example, convert SASS/LESS to CSS, minify JavaScript, etc.
                    sh "npm install" // Install necessary dependencies
                    sh "npm run build" // Execute the build script
                }
            }
        }

        stage('Copy HTML to Tomcat') {
            steps {
                script {
                    def tomcatWebappsDir = "/var/lib/tomcat9/webapps/ROOT/"
                    def htmldir = "html"
                    sh "cp -r ${htmldir}/* ${tomcatWebappsDir}"
                }
            }
        }
    }
}
                       
