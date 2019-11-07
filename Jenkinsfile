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
             sh "docker build -t ${env.ACCOUNT_ID}.dkr.ecr.${env.REGION}.amazonaws.com/sample-app:${env.BUILD_NUMBER} ."
             sh "docker push ${env.ACCOUNT_ID}.dkr.ecr.${env.REGION}.amazonaws.com/sample-app:${env.BUILD_NUMBER}"
         }
      }

    //   stage('Deploy') {
    //      steps {
    //          sh 'docker build .'
    //      }
    //   }

   }
}
