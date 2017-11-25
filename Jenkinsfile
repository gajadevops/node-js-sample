node {
   echo 'Hello World'
   
    stage 'Build'
        cleanWs()
        sh 'git clone https://github.com/gajadevops/node-js-sample.git'
        sh 'cd node-js-sample && pwd'
    
    stage 'Docker image build'
        sh 'cd node-js-sample && pwd'
        sh 'docker build -t nodejs-image-new node-js-sample/Dockerfile'
        
    stage 'Docker image tag'
        sh 'echo $(aws ecr get-login --region us-east-2 --registry-ids 410602862282) > file.txt'
        sh '$( sed "s/-e none//g" file.txt)'
        sh 'docker tag nodejs-image-new 410602862282.dkr.ecr.us-east-2.amazonaws.com/demo-poc:nodejs-image-new-${build_image_version}'
    
    stage 'Docker image push'
        sh 'docker push 410602862282.dkr.ecr.us-east-2.amazonaws.com/demo-poc:nodejs-image-new-${build_image_version}'

    stage 'Kubernetes Deploy'
         sh 'echo Hello'
}


    