pipeline {
   agent any

   stages {
      stage('Preparation') {
         steps {
            git 'git@github.com:gau1991/jenkins-ci-cd-example.git'
         }
      }

      stage('Pylint') {
         steps {
             sh 'pylint blog mysite'
         }
      }

      stage('Test') {
         steps {
             sh 'pylint blog mysite'
         }
      }

      stage('Build') {
         steps {
             sh 'docker build .'
         }
      }

   }
}
