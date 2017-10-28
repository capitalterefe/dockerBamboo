#!/usr/bin/env groovy
node {
   def mvnHome
   
   stage('Preparation') { 
      git 'https://github.com/seleniumBatch2017/dockerBamboo.git'
      mvnHome = tool 'M3'
   }
   
   stage ("Start Selenium Grid"){
    sshagent(['c4725c71-bcfb-49e0-b8fa-58e9e1529dea']) {
    sh 'ssh -tt jenkins@35.196.229.177 /usr/local/bin/start-grid.sh'
   }

   stage('Test') {
      
         sh "'${mvnHome}/bin/mvn' -Dmaven.test.failure.ignore clean verify"
     
   }
   stage('Publish Result') {
     
     publishHTML([allowMissing: false, alwaysLinkToLastBuild: false, keepAll: false, reportDir: 'target/site/serenity', reportFiles: 'index.html', reportName: 'Serenity Report', reportTitles: ''])
   }
   }}
