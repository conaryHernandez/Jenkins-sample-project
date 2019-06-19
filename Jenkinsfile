node {
   stage('Prepare environment') {
        git branch: 'master', url: 'https://github.com/conaryHernandez/testing-jenkins.git'
        sh 'npm install'
    }
    stage('Run tests')  {
        sh 'npm run test'
    }
    stage('Build')  {
        sh 'npm run build'
    }
    stage('Deploy') {
        sh 'echo $JOB_NAME'
        sh 'ssh root@104.131.108.63 echo $JOB_NAME'
        sh 'ssh root@104.131.108.63 rm -rf /var/www/html/$JOB_NAME'
        sh 'ssh root@104.131.108.63 mkdir -p /var/www/html/$JOB_NAME'
        sh 'scp -r build root@104.131.108.63:/var/www/html/$JOB_NAME'
        sh 'ssh root@104.131.108.63 "mv /var/www/html/$JOB_NAME/build/* /var/www/html/$JOB_NAME"'
        sh 'ssh root@104.131.108.63 rm -rf /var/www/html/$JOB_NAME/build/'
        sh 'ssh root@104.131.108.63 ls /var/www/html/ -a'
    }
}