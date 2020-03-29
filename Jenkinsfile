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

                echo "BUILD_NUMBER:           ${env.BUILD_NUMBER}"
                echo "BUILD_ID:           ${env.BUILD_ID}"
                echo "BUILD_DISPLAY_NAME:           ${env.BUILD_DISPLAY_NAME}"
                echo "BUILD_URL:           ${env.BUILD_URL}"
                echo "BUILD_TAG:           ${env.BUILD_TAG}"

                echo "JOB_NAME:           ${env.JOB_NAME}"
                echo "JOB_BASE_NAME:           ${env.JOB_BASE_NAME}"
                echo "JOB_URL:           ${env.JOB_URL}"

                echo "EXECUTOR_NUMBER:           ${env.EXECUTOR_NUMBER}"
                echo "NODE_NAME:           ${env.NODE_NAME}"
                echo "NODE_LABELS:           ${env.NODE_LABELS}"
                echo "WORKSPACE:           ${env.WORKSPACE}"

                echo "JENKINS_HOME:           ${env.JENKINS_HOME}"
                echo "JENKINS_URL:           ${env.JENKINS_URL}"
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
                body:'${SCRIPT, template="groovy-html.template"}',
                // body:"""
                // ${env.JOB_NAME}
                // """,

                attachLog:true,
                compressLog:true,
                attachmentsPattern:'hook_test/*,hook_test/new/*,hook_test/新建文件夹/*',
                ) 
        }
    }
}