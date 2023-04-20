pipeline {
    agent  any;
    stages {
        stage('Preparando el entorno') {
            steps {
                sh 'pip install -r requirements.txt'
            }
        }
        stage('Calidad de código') {
            steps {
                sh 'python3 -m pylint app.py'
            }
        }
        stage('Tests') {
            steps {
                sh 'python3 -m pytest'
            }
        }
   
    stage('Build') {
          agent { 
            node{
              label "DockerServer"; 
              }
          }
          steps {
              sh 'docker build https://github.com/firnstro/jenkins.git -t pipeline:latest'
          }
      }        
      stage('Deploy') {
          agent { 
            node{
              label "DockerServer"; 
              }
          }
          steps {
              sh 'docker run -tdi -p 5000:5000 pipeline:latest'
          }
      }
    }

}
