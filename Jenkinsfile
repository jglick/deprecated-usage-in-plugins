pipeline {
   agent {
      label 'java'
   }

   triggers {
      cron('H H * * *')
   }

   tools {
      jdk 'jdk8'
      maven 'mvn'
   }

   options {
      timeout(time: 1, unit: 'HOURS')
   }

   stages {
      stage ('Checkout') {
         steps {
            checkout scm
         }
      }

      stage ('Build') {
         steps {
            sh 'mvn clean package exec:java'
         }
      }

      stage ('Archive') {
         steps {
            archive 'output/**'
         }
      }
   }
}
