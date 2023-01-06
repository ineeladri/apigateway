node {
      stage("Git Clone"){

        git branch: 'main', url: 'https://github.com/ineeladri/apigateway.git'
    }
   
    stage("Docker build"){
    sh 'docker build -t apigateway:latest -f Dockerfile .'
        sh 'docker image ls'
    }
withCredentials([[$class: 'UsernamePasswordMultiBinding', credentialsId: 'test', usernameVariable: 'apurva09', passwordVariable: 'password']]) {
        sh 'docker login -u apurva09 -p $password'
	}
    stage("Pushing Image to Docker Hub"){
	     sh 'docker tag apigateway apurva09/customer:latest'
	   sh 'docker push apurva09/apigateway:latest'
    }
}
