pipeline {
           agent { label 'worker1' }
           stages {
                stage("Install") {
                     steps {
                          sh 'sudo yum install -y epel-release nodejs'
                          sh 'sudo yum install -y nodejs'
                     }
                }
                stage("Download"){
                    steps {
                        sh 'rm -rf /home/jenkins/worker/workspace/teszt/jenkins/'
                        sh 'git clone https://github.com/tothti/jenkins.git'
                    }
                }
                stage("Copy"){
                    steps {
                        sh 'cp /home/jenkins/worker/workspace/teszt/jenkins/index.js /tmp'
                        sh 'sudo systemctl daemon-reload'
                        sh 'sudo systemctl start index_js'
                    }
                }
                stage("Firewall"){
                    steps {
                        sh 'sudo firewall-cmd --add-port=8888/tcp'
                        sh 'curl 192.168.56.120:8888'
                    }
                }
                    
           }
      }


