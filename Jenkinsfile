pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo "🔧 Setting up Python environment with pipenv"
                sh 'pipenv --python python3 sync'
            }
        }

        stage('Test') {
            steps {
                echo "🧪 Running tests with pytest"
                sh 'pipenv run pytest'
            }
        }

        stage('Package') {
            when {
                anyOf {
                    branch "master"
                    branch "release"
                }
            }
            steps {
                echo "📦 Zipping lib folder into sbdl.zip"
                sh 'zip -r sbdl.zip lib || echo "lib folder not found, skipping zip"'
            }
        }
<<<<<<< HEAD
	stage('Release') {
	   when{
	      branch 'release'
	   }
           steps {
              sh "scp -i /home/Acer/cred/myspark.pem -o 'StrictHostKeyChecking no' -r sbdl.zip log4j.properties sbdl_main.py sbdl_submit.sh conf ubuntu@13.204.43.138:/home/ubuntu/sbdl-qa"
           }
        }
	stage('Deploy') {
	   when{
	      branch 'master'
	   }
           steps {
               sh "scp -i /home/Acer/cred/myspark.pem -o 'StrictHostKeyChecking no' -r sbdl.zip log4j.properties sbdl_main.py sbdl_submit.sh conf ubuntu@13.204.43.138:/home/ubuntu/sbdl-prod"
           }
=======

        stage('Release') {
            when {
                branch 'release'
            }
            steps {
                echo "🚀 [Simulated] Releasing to QA environment (would SCP files here)"
                sh 'mkdir -p /tmp/sbdl-qa && cp -r sbdl.zip log4j.properties sbdl_main.py sbdl_submit.sh conf /tmp/sbdl-qa || echo "Some files missing, skipped copy"'
            }
        }

        stage('Deploy') {
            when {
                branch 'master'
            }
            steps {
                echo "🚀 [Simulated] Deploying to PROD environment (would SCP files here)"
                sh 'mkdir -p /tmp/sbdl-prod && cp -r sbdl.zip log4j.properties sbdl_main.py sbdl_submit.sh conf /tmp/sbdl-prod || echo "Some files missing, skipped copy"'
            }
>>>>>>> f5ba6b11e95aef2c2e386a573d73b0af5687bab8
        }
    }
}
