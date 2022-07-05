pipeline
{
  agent none
  stages{
    stage ('Clone Git Repository')   
    {
      agent {label 'docker'}
      steps
      {
        git branch: 'main', url: 'https://github.com/mottythomas/docker.git'
        sh 'echo git clone completed successfully'
      }
    }
    stage ('Docker Image Build and Push to Repo')
    {
      agent {label 'docker'}
      steps
      {
       sh 'docker build -t mottythomas/webapp .' 
       sh 'docker push mottythomas/webapp'
      }
    }
    stage ('Docker Container Deploy')
    {
      agent {label 'master'}
      steps
      {
        sh 'docker rm -f webapp'
        sh 'docker run --name webapp -idt -p 8090:80 mottythomas/webapp'
      }
    }
  }
}
