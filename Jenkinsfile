node('linux'){
    stage('Test'){
        git 'https://github.com/zhusyx/java-project.git'
        sh 'ant -buildfile test.xml'
    }
    
    stage('Build'){
        sh 'ant'
    }
    
    stage('Results'){
        junit 'reports/*.xml'
    }
}
