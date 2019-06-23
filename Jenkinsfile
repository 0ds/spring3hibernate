properties([parameters([choice(choices: ['master', 'branch1', 'branch2'], description: 'select branch', name: 'branch_choise')])])

node{
 
      stage('SCM checkout')
    {
       git url: 'https://github.com/0ds/spring3hibernate.git', branch: "${branch_choise}"
    }
      stage('Auth check')
    {
      input message: 'Enter your ID', ok: 'Enter', submitter: 'admin,vishal', submitterParameter: 'ID'  
     }
}
