node {
   echo 'Hello World'
   git 'https://github.com/gajadevops/node-js-sample.git'
   
    stage 'Build'
        sh 'sudo rm -rf node-js-sample'
        sh 'git clone https://github.com/gajadevops/node-js-sample.git'
        sh 'cd node-js-sample && pwd'
    
    stage 'Docker image build'
        sh 'cd /var/lib/jenkins/workspace/nodejs-pipeline/node-js-sample/'
        sh 'sudo docker build -t nodejs-image-new .'
        
    stage 'Docker image tag'
        sh 'echo $(aws ecr get-login --region us-east-2 --registry-ids 410602862282) > file.txt'
        sh 'sudo $( sed "s/-e none//g" file.txt)'
        sh 'sudo  docker tag nodejs-image-new 410602862282.dkr.ecr.us-east-2.amazonaws.com/demo-poc:nodejs-image-new-${build_image_version}'
    
    stage 'Docker image push'
        sh 'sudo docker push 410602862282.dkr.ecr.us-east-2.amazonaws.com/demo-poc:nodejs-image-new-${build_image_version}'

    stage 'Kubernetes Deploy'
         sh 'echo Hello'
#        sh 'kubectl get pods'
#        sh 'kubectl create -f /var/lib/jenkins/workspace/docker-build/node-js-sample/service.yml'
#        sh 'kubectl create -f /var/lib/jenkins/workspace/docker-build/node-js-sample/deploy.yml'
#        sh 'kubectl get pods'
}
    