pipeline
{
  agent docker
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
    stage ('Docker Image Build and Push to Repo')
    {
      steps
      {
       sh 'docker build -t 192.168.10.100:8080/staging/myweb .' 
       sh 'docker push 192.168.10.100:8080/staging/myweb'
      }
    }
    
  }
}
