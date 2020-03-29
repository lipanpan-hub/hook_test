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

                ) 
        }
    }
}