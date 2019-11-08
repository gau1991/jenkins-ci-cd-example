pipeline {
   agent any

   stages {
      stage('Preparation') {
         steps {
            git 'git@github.com:gau1991/jenkins-ci-cd-example.git'
         }
      }

      stage('Linter') {
         steps {
             sh 'pylint blog mysite'
         }
      }

      stage('Test') {
         steps {
             sh 'python3 manage.py test'
         }
      }

      stage('Build') {
         steps {
             sh "docker build -t gau1991/sample-app:${env.BUILD_NUMBER} ."
             sh "docker push gau1991/sample-app:${env.BUILD_NUMBER}"
         }
      }

      stage('Deploy') {
         steps {
             sh 'kubectl set image deployments/myserver myserver=gau1991/sample-app:${env.BUILD_NUMBER}'
         }
      }
   }
}
