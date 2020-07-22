pipeline {
	agent any


	stages {
	    stage('Git Checkout'){
	       steps {
	         git 'https://github.com/narulsa1/django-app'
	       }     
	    }
         
        stage('Configuration'){
           steps{
           sh 'python -m pip install --user virtualenv'
           sh 'python -m venv env'
           sh 'source env/bin/activate'
           sh 'pip install -r requirements.txt'
           } 

        }
        stage('Unit Test'){
           steps{
              sh 'cd app'
              sh 'python manage.py makemigrations'
              sh 'python manage.py migrate'
              sh 'python manage.py test'
            }
 	      }
 	      stage('Checklist') {
 	         steps {
 	            sh 'cd app'
              sh 'python manage.py check --deploy'
 	         }
 	      }
        stage('Style check') {
           steps{
              sh 'pip install flake8'
              sh 'flake8 app/ --max-line-length=127'
           }
    }

  }
}
