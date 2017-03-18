pipeline {
   agent {
      label 'java'
   }

   triggers {
      cron('H H * * *')
   }

   environment {
      tool 'jdk8'
      tool 'mvn'
   }

   options {
      timeout(time: 1, unit: 'HOURS')
   }

   stages {
      stage 'Checkout' {
         git 'https://github.com/jenkins-infra/deprecated-usage-in-plugins.git'
      }

      stage 'Build' {
         sh 'mvn clean package exec:java'
      }

      stage 'Archive' {
         archive 'target/*.html'
      }
   }
}
