
stage "Pull"
  checkout scm

stage "Init docker"
  sh "docker stop node && docker rm node"
  sh "docker run -di -v /home/docker/jenkins_home/workspace/node/helloworld/:/var/nodebuild -w /var/nodebuild --name node nodebuild"
  sh "docker exec -ti node /bin/bash"
  sh "echo Docker up and running with volume mounted."
  
stage "NPM"
  sh "echo installing npm dependencies..."

stage "Bower"
  sh "echo installing bower dependencies..."

