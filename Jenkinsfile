
node {
  stage 'Pull'
    checkout scm
    sh 'echo On branch: $BRANCH_NAME'
    sh 'echo Job name: $JOB_NAME'

    
  stage 'Init docker'
    // The exit 0 makes sure that if the containers are already removed/down, the build continues
    sh 'docker stop node | exit 0'
    sh 'docker rm node | exit 0'
    // the path provided for workspace/job is not the path INSIDE the Jenkins container but the path on the actual host the Jenkins container is running on -- UGH!
    sh 'docker run -di -v /home/docker/jenkins_home/workspace/$JOB_NAME/:/var/nodebuild -w /var/nodebuild --name node nodebuild'
    sh 'echo Docker up and running with volume mounted.'

    
  stage 'NPM'
    sh 'echo installing npm dependencies...'
    sh 'docker exec node ls'
  
  stage 'Bower'
    sh 'echo installing bower dependencies...'

  
}
