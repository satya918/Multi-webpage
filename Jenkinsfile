pipeline {
    agent any
    
    stages {
        stage('Checkout') {
            steps {
                checkout scm
            }
        }
        
        stage('Deploy to Tomcat') {
            steps {
                script {
                    // Define the path to your Tomcat webapps directory
                    def tomcatWebapps = "/var/lib/tomcat9/webapps"
                    
                    // Directory where your HTML files are located
                    def htmlDir = "html"
                    
                    // Deploy each HTML file to Tomcat webapps directory
                    sh "cp -r ${htmlDir}/* ${/var/lib/tomcat9/webapps}/"
                }
            }
        }
    }
}
