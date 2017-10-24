#!/usr/bin/env groovy
node {
   def mvnHome
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/seleniumBatch2017/dockerBamboo.git'
      
                 
      mvnHome = tool 'M3'
   }
    stage('Start Selenium Grid') {

                sh "docker-compose up -d"
     }
   stage('Test') {
      
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean verify"
     
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
   }
}