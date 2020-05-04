pipeline {
           agent { label 'worker1' }
           stages {
                stage("Install") {
                     steps {
                          sh 'sudo yum install -y epel-release'
                          sh 'sudo yum install -y nodejs'
                     }
                }
                stage("Download"){
                    steps {
                        sh 'rm -rf /home/jenkins/worker/workspace/github/jenkins/'
                        sh 'git clone https://github.com/tothti/jenkins.git'
                        sh 'sudo cp /home/jenkins/worker/workspace/github/index_js.service /lib/systemd/system'
                    }
                }
                stage("Copy"){
                    steps {
                        sh 'cp /home/jenkins/worker/workspace/github/jenkins/index.js /tmp'
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
