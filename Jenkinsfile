node('linux'){
    stage('Test'){
        git 'https://github.com/zhusyx/java-project.git'
        sh 'ant'
        sh 'ant -f test.xml -v'
        junit 'reports/result.xml'
    }
    
    stage('Build'){
        sh 'ant'
        ant -f build.xml -v 
    }
    
    
    
    stage('Report'){
        junit 'reports/*.xml'
        sh 'aws cloudformation describestack-resources --region us-east-1 --stack-name jenkins'
    }
}

