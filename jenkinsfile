pipeline{
    
    stage('git checkout')
    {
    git 'https://github.com/g0t4/jenkins2-course-spring-boot.git'
    }
    stage('Maven Build') {
    dir('spring-boot-samples/spring-boot-sample-atmosphere') {
    sh 'mvn clean package'
    step([$class: 'JUnitResultArchiver',
    testResults: 'target/surefire-reports/TEST-sample.atmosphere.SampleAtmosphereApplicationTests.xml'])
    }

    stage('Archiving jar') {
    archiveArtifacts 'spring-boot-samples/spring-boot-sample-atmosphere/target/*.jar'
    }
    stage("Jacoco Reports"){
        publishHTML([allowMissing: false, 
    alwaysLinkToLastBuild: true, 
    keepAll: false, 
    reportDir: 'spring-boot-samples/spring-boot-sample-atmosphere/target/site/jacoco', 
    reportFiles: 'index.html', 
    reportName: 'HTML Report', 
    reportTitles: ''])
    }

}


}
