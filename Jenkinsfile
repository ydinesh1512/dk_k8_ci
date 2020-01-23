node{
  def Namespace = "pkapp"
  def ImageName = "maheshkharwadkar/mkimage"
  def Creds	= "mk-dockerhub-creds"
  def imageTag = "1.0"
  stage ('checkout'){
	git 'https://github.com/maheshkharwadkar/mk-k8-ci-cd.git'
  }
  stage ('Run Unit Test'){
	sh "npm install"
	sh "npm test"
  }

  stage('Docker Build, Push'){
    withDockerRegistry([credentialsId: "${Creds}", url: 'https://index.docker.io/v1/']) {
      sh "docker build -t ${ImageName}:${imageTag} ."
      sh "docker push ${ImageName}"
        }

    }
  
}