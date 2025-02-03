pipeline {
    agent any  // Run on any available agent

    stages {
        
        stage('Clearing previous cont & images form system node') {
            
            steps {
                echo 'Stoping all running containers'
                sh 'docker stop $(docker ps -q) || docker kill $(docker ps -q)'
                
                echo 'Deleting all containers!!!'
                sh 'docker rm $(docker ps -aq)'
                
                echo 'Deleting all exiting images !!!'
               sh 'docker rmi $(docker images -q)' 
            
                
            }
        }
             

        
        stage('Checkout Code') { // Descriptive stage name
            steps {
                echo 'Cloning code from GitHub...'
                git url: 'https://github.com/Bijendar/multi-project.git', branch: 'main'
                echo 'Code cloned successfully!'
            }
        }

        stage('Build Image') { // Descriptive stage name
            steps {
                echo 'Building Docker image...'
                sh 'docker build -t multi-project:latest .'
                echo 'Image build complete!'
            }
        }

        stage('Run Tests') { // Descriptive stage name (assuming you have tests)
            steps {
                echo 'Running tests...'
                // Add commands to run your tests here (e.g., sh 'mvn test' or 'npm test')
                echo 'Tests completed!'  // Add conditional logic based on test results (optional)
            }
        }

        stage('Deploy') { // Descriptive stage name
            steps {
                echo 'Deploying application...'
                sh 'docker run -d -p 80:80 multi-project:latest'
                echo 'Deployment successful!'
            }
        }
    }
}
