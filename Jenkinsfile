pipeline {
    agent any

    stages {
        stage('git') {
            steps {
                git branch: 'main', url: 'https://github.com/MUTHUMMK/AUTOMATION.git'
            }
        }
        stage('build_image & push') {
            steps {
                script{
                    sh "sh build.sh "
                }
            }
        }
        stage('deploy') {
            steps {
                script{
                    withCredentials([sshUserPrivateKey(credentialsId: 'sskkey', keyFileVariable: 'sshkeyvar', usernameVariable: 'ssh')]) {
                        
                        sh 'sh deploy.sh $sshkeyvar'
                        
}
                }
            }
        }
    }
}
