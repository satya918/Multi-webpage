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
                    def htmldir = "html"
                    dir("${workspace}/${htmldir}") {
                        // Run npm install in the "html" directory where package.json is located
                        sh "npm install"
                        // Add additional build steps here, if needed
                    }
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
