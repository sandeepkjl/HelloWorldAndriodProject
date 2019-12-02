pipeline {
    agent any



stages{
        stage('init'){
            steps{
                echo 'initialization...'
            }
        }
		
        stage('Build'){
            
            steps {
                sh 'chmod +x ./gradlew'  
                sh './gradlew assembledebug'
                                                
            }
        }
}
}