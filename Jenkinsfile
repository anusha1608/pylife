pipeline {
    agent {
        node {
            label 'java11'
        }
    
    }

    // options {
    //             timestamps()
    //             buildDiscarder(logRotator(numToKeepStr: '5', artifactNumToKeepStr: '2'))
    //             timeout(time: 240, unit: 'MINUTES')
    //            // disableConcurrentBuilds()
    //             }

        stages {
            stage ('AppCodeCheckout') {
                steps {

                    git 'https://github.com/anusha1608/pylife.git'

                }
            }
            stage ('CI Build') {

                steps {

                    sh 'mvn clean package'
                   
                     }
    
            }

            stage ('Docker Build && Push && DEPLOY ') {
               

                steps {
                    // withCredentials([string(credentialsId: 'DOCKERPWD', variable: 'DOCKER_TOKEN')]) {
                    withCredentials([string(credentialsId: '', variable: 'DOCKERPWD')]) {


                    sh 'docker build . -t anusha1659594/pylife:latest'
                    sh 'docker login -u anusha1659594 -p dckr_pat_CHou9p06CRc2N6FL4RFL7bNvw8s'
                    sh 'docker push anusha1659594/pylife:latest'
                    sh 'docker run -p 89:8080 -d anusha1659594/pylife:latest'
                }

                }
            
        }

            // stage('Archive and clean workspace') {
            //     steps {
                    
            //         archiveArtifacts artifacts: 'target/*.jar', followSymlinks: false
            //         cleanWs()
            //     }

            // }
        }  
}