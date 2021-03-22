pipeline {
	    agent any
	    stages {
	        stage('Checkout') {
	            steps{
	                checkout scm
	            }
	        }
	        stage('Test') {
	            steps{
	                sh "ls -latr"
	            }
	        }
            stage('Copy'){
                steps{
                    withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'awscred', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
                        sh "/usr/local/bin/aws s3 ls"
			sh "/usr/local/bin/aws s3 sync . s3://jenkinsatit/jenkinsassignment/ --delete "
                   }
                }
            }
	    }
	}

