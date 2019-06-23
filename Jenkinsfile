properties([parameters([choice(choices: ['master', 'branch1', 'branch2'], description: 'select branch', name: 'branch_choise')])])

node{
  
      stage('email-notification'){
          mail bcc: '', body: 'Built Fail', cc: '', from: '', replyTo: '', subject: 'Jenkins report', to: "${_MY_EMAIL}"
}
      stage('SCM checkout')
    {
       git url: 'https://github.com/0ds/spring3hibernate.git', branch: "${branch_choise}"
    }
      stage('Auth check')
    {
      input message: 'Enter your ID', ok: 'Enter', submitter: 'admin,vishal', submitterParameter: 'ID'  
     }
      
 
       parallel firstbranch: {
       stage('compile-package')
       {
     def mvnHome = tool name: 'maven 3.6.1', type: 'maven'
      sh "${mvnHome}/bin/mvn  -B -DskipTests clean package"
      }
       }, secondbranch: {
       stage('checkstyle'){
          def mvnHome = tool name: 'maven 3.6.0', type: 'maven'
           sh "${mvnHome}/bin/mvn checkstyle:checkstyle"
          checkstyle canComputeNew: false, defaultEncoding: '', healthy: '', pattern: '', unHealthy: ''
       }
}, failFast: false
}
