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

         stage('upload to artifactory'){
            steps{
                rtUpload (
                    serverId: 'JfrogRepository',
                    spec: '''{
                        "files": [
                            {
                                "pattern": "./app/build/outputs/apk/*.apk",
                                "target": "libs-snapshot-local/"
                            }
                                ]
                        }''',
 
                    // Optional - Associate the uploaded files with the following custom build name and build number,
                    // as build artifacts.
                    // If not set, the files will be associated with the default build name and build number (i.e the
                    // the Jenkins job name and number).
                    buildName: 'JFrog',
                    buildNumber: env.BUILD_NUMBER )
            }
        }
}
}