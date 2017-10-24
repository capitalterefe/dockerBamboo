#!/usr/bin/env groovy
node {
   def mvnHome
   stage('Preparation') { 
      git 'https://github.com/seleniumBatch2017/dockerBamboo.git'
      
                 
      mvnHome = tool 'M3'
   }
   stage "Run container"
node {
    sh 'docker-compose  -f docker-compose.yml up -d'
}
    
   stage('Test') {
      
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean verify"
     
   }
   stage('Results') {
      junit '**/target/surefire-reports/TEST-*.xml'
   }
}