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
        stage("Disp ENV"){
            steps{
                echo "${env.BRANCH_NAME}"
                echo "${env.CHANGE_ID}"
                echo "${env.CHANGE_URL}"
                echo "${env.CHANGE_TITLE}"
                echo "${env.CHANGE_AUTHOR}"
                echo "${env.CHANGE_AUTHOR_DISPLAY_NAME}"
                echo "${env.CHANGE_AUTHOR_EMAIL}"
                echo "${env.CHANGE_TARGET}"
                echo "${env.CHANGE_BRANCH}"
                echo "${env.CHANGE_FORK}"

                echo "${env.BUILD_NUMBER}"
                echo "${env.BUILD_ID}"
                echo "${env.BUILD_DISPLAY_NAME}"
                echo "${env.BUILD_URL}"
                echo "${env.BUILD_TAG}"

                echo "${env.JOB_NAME}"
                echo "${env.JOB_BASE_NAME}"
                echo "${env.JOB_URL}"

                echo "${env.EXECUTOR_NUMBER}"
                echo "${env.NODE_NAME}"
                echo "${env.NODE_LABELS}"
                echo "${env.WORKSPACE}"

                echo "${env.JENKINS_HOME}"
                echo "${env.JENKINS_URL}"
            }
        }
    }

    post{
        always{
            emailext(
                subject:"rmhunter 测试结果报告",
                mimeType:"text/html",
                from:"lipanpanmail@163.com",
                to:"lipanpanmail@163.com",
                replyTo:"do-not-reply@dji.com",
                body:"""
                ${env.JOB_NAME}
                """,


                attachLog:true,
                compressLog:false,
                attachmentsPattern:"${env.WORKSPACE}/*.txt"
                ) 
        }
    }
}