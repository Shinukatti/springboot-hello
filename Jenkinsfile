pipeline {
    agent any
    stages {
        stage('clone_scm') {
            steps {
               echo 'Cloning the Git repository...'
                git url: 'https://github.com/Shinukatti/springboot-hello.git', credentialsId: 'your-credentials-id', branch: 'main'
            }
        }
        stage('maven_build') {
            steps {
                sh 'mvn clean package -DskipTests'
            }
            post {
                success {
                    echo 'Build is success'
                }
            }
        }
            
        stage('copy backup') {
            steps {
                sh 'sudo -i'
                sh 'sudo cp -r /home/jenkins/jenkins_root/workspace/demo1/ /home/ubuntu/'
            }
        }
    }
        
    post {
        success {
            mail to: 'ck.shrinivas5@gmail.com',
                 subject: 'Build successful',
                 body: 'Congratulations! Your build succeeded.'
        }
        failure {
            // Send email notification when the build fails
            mail to: 'ck.shrinivas5@gmail.com',
                 subject: 'Build failed',
                 body: 'Sorry, your build failed. Please check the console output for more details.'
        }
    }
 } 
