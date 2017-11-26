node {
   echo 'Hello World'
   
    stage 'Build'
        cleanWs()
        sh 'git clone https://github.com/gajadevops/node-js-sample.git'
        sh 'cd node-js-sample && pwd'
    
    stage 'Docker image build'
        sh 'cd node-js-sample && pwd'
        sh 'cd node-js-sample && sudo docker build -t nodejs-image-new .'
        
    stage 'Docker image tag'
        sh 'echo $(aws ecr get-login --region us-east-2 --registry-ids 410602862282) > file.txt'
        sh '$( sed "s/-e none//g" file.txt)'
        sh 'sudo docker tag nodejs-image-new 410602862282.dkr.ecr.us-east-2.amazonaws.com/demo-poc:nodejs-image-new-${BUILD_NUMBER}'
    
    stage 'Docker image push'
        sh 'sudo docker push 410602862282.dkr.ecr.us-east-2.amazonaws.com/demo-poc:nodejs-image-new-${BUILD_NUMBER}'

    stage 'Kubernetes Deploy'
         sh 'echo Hello'
        sh 'kubectl replace -f node-js-sample/service.yml --record'
        sh 'kubectl replace -f node-js-sample/deploy.yml --record'
        sh 'kubectl rollout status deployment nodejs'
        sh 'kubectl get pods'
        sh 'kubectl rollout status deployment nodejs'
}


    