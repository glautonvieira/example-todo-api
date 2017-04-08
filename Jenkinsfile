node('php'){
    stage('Clean'){
        deleteDir()
        sh 'ls -la'
    }
    
    stage('Fetch') {
        git 'https://github.com/glautonvieira/example-todo-api.git'
    }
    
    stage('Build'){
        sh 'composer install --prefer-dist --no-dev --ignore-platform-reqs'
        sh 'php artisan config:cache'
        // sh 'php artisan route:cache'
    }
    
    stage('Docker Build') {
        sh 'sudo docker build -t glautonvieira/todoapi:$BUILD_NUMBER .'
    }
    
    stage('Docker Ship') {
        sh 'sudo docker push glautonvieira/todoapi:$BUILD_NUMBER'
    }
}
