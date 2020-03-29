pipeline {
    agent {label 'windows'}
 
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                bat(script:"echo %date%-%time%")
                bat(script:"dir .")

                deleteDir()
                bat(script:"dir .")
                
                bat(script:"git clone https://github.com/lipanpan-hub/hook_test.git")
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}