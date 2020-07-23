pipeline {
	agent any

	   

	stages {
	      stage('Git Checkout'){
	         steps {
	            git 'https://github.com/narulsa1/django-app'
	          }     
	      }
         
<<<<<<< HEAD
=======
        stage('Configuration'){
           steps{
           sh 'python -m pip install --user virtualenv'
           sh 'python -m virtualenv env'
           sh 'source env/bin/activate'
           sh 'pip install -r requirements.txt'
           } 
>>>>>>> 1764258a7d53130a79b628d329b8d42e03b0d8ff

        
        stage('Build Docker Image'){
           steps{
              sh 'docker images -a | grep "django-app" | awk '{print $3}'| xargs docker rmi -f'
              sh 'docker build -t django-app .'
            }
 	      }
 	      stage('Push Docker Image') {
 	         steps {
              withCredentials([usernameColonPassword(credentialsId: 'dockerhub', variable: 'dockerhubPwd')]) {
                sh 'docker login -u snarula -p ${dockerhubPwd}'
               }
            }
 	      }
        stage('Docker container') {
           steps{
              sh 'docker run -itd -p 8020:8020 -e  DJANGO_SUPERUSER_USERNAME=admin -e DJANGO_SUPERUSER_PASSWORD=sekret1 -e DJANGO_SUPERUSER_EMAIL=admin@example.com django-app'
            }
       }

  }
}
