pipeline{
   agent any
   stages{
     stage('checkin from github'){
       steps{
	   git credentialsId: 'Abhinandh-GitHub', url: 'https://github.com/abhinandh/sampleCICD.git'
       }
     }
	 stage('creatin docker image'){
      steps{
	  sh "sudo docker build /var/lib/jenkins/workspace/SamplePythonProject -t abhinandh1991/samplepython_1:firstapp"
      }
     }
	 stage('docker image push'){
	steps{
	  withCredentials([string(credentialsId: 'abhinandh1991-abkc', variable: 'testDocker')]) {
          sh "sudo docker login -u abhinandh1991 -p ${testDocker} docker.io"
	  sh "sudo docker push docker.io/abhinandh1991/samplepython_1:firstapp"
		}
	  }
     } 
	   stage('Run the docker container'){
        steps{
          	 sh "sudo docker run -d --name firstpython -p 50005:5000 abhinandh1991/samplepython_1:firstapp"  

	   }
     }
   }	   
}
