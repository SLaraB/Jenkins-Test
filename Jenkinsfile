pipeline{
        stage('Deploy'){
            agent {
                label 'master'
            }
            options {
                skipDefaultCheckout()
            }
            steps {
                sh 'docker stop server || true'
                sh 'docker rm server || true'
                sh 'rm -rf /jenkins-test/'
                sh 'git clone https://github.com/slarab/jenkins-test'
                sh 'docker run -dit --name server -p 80:80 -v /jenkins-test/public/:/usr/local/apache2/htdocs/ httpd:2.4'
            }
        }
    }
}

