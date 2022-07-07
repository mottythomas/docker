pipeline
{
  agent {label 'docker'}
  stages
  {
    stage ('Clone Git Repository')
    {
      steps
      {
        git branch: 'main', url: 'https://github.com/mottythomas/docker.git'
        sh 'echo git clone completed successfully'
      }
    }
    stage ('Docker Image Build')
    {
      steps
      {
       sh 'docker build -t 192.168.10.100:8080/staging/myweb .' 
       
      }
    }
    stage ('Docker Image Push to Repo')
    {
     steps
      {
         withCredentials([string(credentialsId: 'repopwd', variable: 'repopwd')]) 
          {
            sh "docker login 192.168.10.100:8080 -u admin -p ${repopwd}"
          }
        sh 'docker push 192.168.10.100:8080/staging/myweb' 
      }
       
      }
    stage ('Deploy to Swam Cluster')
    {
      steps
      {
        sshagent(['prodsvr'])
                {
                  sh 'ssh -o StrictHostKeyChecking=no prodadmin@192.168.10.151 bash /home/prodadmin/staging/myweb/deploy-myweb.sh'
                 }
        
      }
    }
    }
    
  }

