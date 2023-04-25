pipeline {
    agent any
    stages {

        stage('Preparando el entorno') {
            agent { 
            node{
              label "objetivo1"; 
              }
          }
            steps {
                sh 'whoami'
                sh 'hostname'
                sh 'python3 -m pip install -r requirements.txt'
            }
        }
        stage('Calidad de código') {
            agent {
                node {
                    label "objetivo1";
                }
            }
            steps {
                 sh 'whoami'
                sh 'hostname'
                sh 'python3 -m pylint app.py'
            }
        }
        stage('Tests') {
             agent {
                node {
                    label "objetivo1";
                }
            }           
            steps {
                sh 'whoami'
                sh 'hostname'
                sh 'python3 -m pytest'
            }
        }
   
    stage('construcción del artefacto') {
          agent { 
            node{
              label "objetivo2"; 
              }
          }
          steps {
              sh 'whoami'
              sh 'hostname'
              sh 'docker build https://github.com/firnstro/jenkins.git -t richijenkins:latest'
          }
      }        
      stage('Despliegue') {
          agent { 
            node{
              label "objetivo2"; 
              }
          }
          steps {
              sh 'whoami'
              sh 'hostname'
              sh 'docker run --name richiapp -tdi -p 5000:5000 richijenkins:latest'
          }
      }
    }

}
