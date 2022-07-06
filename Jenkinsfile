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
            sh "doker login -u admin -p ${repopwd}"
          }
        sh 'docker push 192.168.10.100:8080/staging/myweb' 
      }
       
      }
    }
    
  }
}
