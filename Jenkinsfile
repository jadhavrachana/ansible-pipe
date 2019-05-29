pipeline {

    agent any

    stages {

        stage('SCM') {

            steps {
                    git "https://github.com/jadhavrachana/ansible-pipe.git"
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
                   sh "scp tomcat.yml root@192.168.1.101:/etc/ansible/"
                 sh 'ssh root@192.168.1.101 "ansible-playbook /etc/ansible/tomcat.yml"'
                  sh "scp /var/lib/jenkins/workspace/ansible-pipe/target/wwp-1.0-SNAPSHOT.war root@192.168.1.101:/tomcat"
                   sh "scp copy.yml root@192.168.1.101:/etc/ansible/"
                   sh 'ssh root@192.168.1.101 "ansible-playbook /etc/ansible/copy.yml"'

                //
            }
       }


    }
}



