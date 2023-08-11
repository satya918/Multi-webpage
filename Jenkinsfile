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
                    
                    // Verify if the tomcatWebapps directory exists
                    if (!fileExists(tomcatWebapps)) {
                        error("Tomcat webapps directory does not exist: ${tomcatWebapps}")
                    }
                    
                    // Verify if the htmlDir directory exists
                    if (!fileExists(htmlDir)) {
                        error("HTML directory does not exist: ${htmlDir}")
                    }
                    
                    // Deploy each HTML file to Tomcat webapps directory
                    sh "cp -r ${htmlDir}/* ${tomcatWebapps}/"
                }
            }
        }
    }
}

def fileExists(path) {
    return file(path).exists()
}
