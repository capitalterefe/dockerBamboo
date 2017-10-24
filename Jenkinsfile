#!/usr/bin/env groovy
node {
   def mvnHome
   stage('Preparation') { // for display purposes
      // Get some code from a GitHub repository
      git 'https://github.com/seleniumBatch2017/dockerBamboo.git'
      sh 'ssh  capital_terefe@35.196.229.177 /home/capital_terefe/selenium_grid_project/grid-service/start-grid.sh'
      
                 
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