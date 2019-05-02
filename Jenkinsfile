
node('linux'){
    stage('Test'){
        git 'https://github.com/zhusyx/java-project'
        sh 'ant -f test.xml -v'
        junit 'reports/result.xml'
    }
    
    stage('Build'){
        sh 'ant -f build.xml -v'
         
    }
    
    stage('Deploy'){
          sh 'aws s3 cp /workspace/java-pipeline/dist/rectangle-${BUILD_NUMBER}.jar s3://seis665cz'  
    }
    
    
    stage('Report'){
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: '73d03e92-0594-424f-b330-f23eb4ef94f3', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]) {
            // some block
            sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
       }

        
    }
}
