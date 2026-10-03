pipeline {

    agent any

    stages {

        stage('Basic Commands') {
            steps {
                bat '''
                    echo ==============================
                    echo Current Directory
                    echo ==============================
                    cd

                    echo ==============================
                    echo Hostname
                    echo ==============================
                    hostname

                    echo ==============================
                    echo Files in Workspace
                    echo ==============================
                    dir
                '''
            }
        }

        stage('PR Test') {
            when {
                changeRequest()
            }

            steps {
                echo "This is a Pull Request build."

                bat '''
                    echo ==============================
                    echo Running PR Test
                    echo ==============================
                    echo PR validation successful
                '''
            }
        }

        stage('Deploy to Main') {
            when {
                branch 'main'
            }

            steps {
                echo "This is MAIN. Copying files to deployment directory."

                bat '''
                    echo ==============================
                    echo Creating deployment directory
                    echo ==============================

                    if not exist "C:\\Users\\teams\\Desktop\\deploy" mkdir "C:\\Users\\teams\\Desktop\\deploy"

                    echo ==============================
                    echo Copying files
                    echo ==============================

                    robocopy . "C:\\Users\\teams\\Desktop\\deploy" /E /XD .git

                    echo ==============================
                    echo Deployment completed
                    echo ==============================
                '''
            }
        }
    }
}