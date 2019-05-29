pipeline {

    agent any

    stages {

        stage('SCM') {

            steps {
                    git "https://github.com/jadhavrachana/tomcat.git"
                //
            }
        }

        stage('Test') {

            steps {
                    sh "mvn test"
                //
            }
        }

        stage('code analysis') {

            steps {
                    sh "/sonar_scanner/bin/sonar-scanner"
                //
            }
        }

        stage('artifact uploader') {

            steps {
                    sh "mvn clean deploy"
                //
            }
       }
       stage('ansible') {

            steps {
                    sh "scp "
                //
            }
       }


      stage ('Deploy') {

            steps {
               sh "scp target/*.war root@192.168.1.101:/var/lib/tomcat/webapps"

            }

        }

    }
}



