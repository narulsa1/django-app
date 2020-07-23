pipeline {
	agent any
 
	stages {
	      stage('Git Checkout'){
	         steps{
	            git 'https://github.com/narulsa1/django-app'
	         }     
	      }
         

        
              stage('Build Docker Image'){
                 steps{
                    sh "docker rmi -f django-app"
                    sh "docker build -t django-app ."
                 }
 	      }

              stage('Docker container') {
                 steps{
                    sh "docker run -itd -p 8020:8020 -e  DJANGO_SUPERUSER_USERNAME=admin -e DJANGO_SUPERUSER_PASSWORD=sekret1 -e DJANGO_SUPERUSER_EMAIL=admin@example.com django-app"
                 }
              }

        }
}

