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
	   sh "sudo docker build /var/lib/jenkins/workspace/SamplePythonProject -t firstapp"
       }
     }
   }	   
}

