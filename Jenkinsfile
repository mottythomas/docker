pipeline
{
  agent any
  stages{
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
       sh 'docker build -t webapp .' 
      }
    }
  }
}
