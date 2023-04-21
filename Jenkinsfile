pipeline {
    agent  any;
    stages {
        stage('Preparando el entorno') {
            steps {
                sh 'echo fase 1'
            }
        }
        stage('Calidad de código') {
            steps {
                sh 'echo fase 2'
            }
        }
        stage('Tests') {
            steps {
                sh 'echo fase 3'
            }
        }
   
    stage('Build') {
          steps {
              sh 'echo fase 4'
          }
      }        
      stage('Delivery') {
          steps {
              sh 'echo fase 5'
          }
      }
    stage('Deploy') {
	steps {
	   sh ' echo fse 6'
	}
    }
    }

}

