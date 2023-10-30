node('appserver-cweb-2140')
{
  def app
  stage('Cloing Git')
  {
    checkout scm
  }
  stage('Build and Tag')
  {
    app = docker.build("hancooj/real-estate-cweb2140")
  }
  stage('Push to Dockerhub')
  {
    docker.withRegistry('https://registry.hub.docker.com', 'dockerhub_credentials')
    {
      app.push('latest')
    }
  }
  stage('Pull Image Server')
  {
    sh "docker-compose down"
    sh "docker-compose up -d"
  }
}
