pipeline {
    agent any
    
    tools {
        maven 'localMaven'
    }
    // parameters {
    //     string(name: 'tomcat_dev',defaultValue:'18.207.188.242',description:'Staging Server')
    //     string(name: 'tomcat_prod',defaultValue:'3.82.105.238',description:'Production Server')
    // }
    
    // triggers {
    //     pollSCM('* * * * *')
    // }
    stages { 

         stage('Build'){
            steps {
                sh 'mvn clean package'
                sh "docker build . -t tomcatwebapp:${env.BUILD_ID}"
            }
            // post {
            //     success {
            //         echo 'Now Archiving...'
            //         archiveArtifacts artifacts: '**/target/*.war'
            //     }
            // }
        }       

        // stage('Deployments') {
        //     parallel{
        //         stage ('Deployment to Staging'){
        //             steps {
        //                 sh "scp -i /Users/Shared/Jenkins/TomcatDemo.pem **/target/*.war ec2-user@${params.tomcat_dev}:/var/lib/tomcat7/webapps"
        //             }
        //         }

        //         stage ('Deployment to Production'){
        //             steps {
        //                 sh "scp -i /Users/Shared/Jenkins/TomcatDemo.pem **/target/*.war ec2-user@${params.tomcat_prod}:/var/lib/tomcat7/webapps"
        //             }
        //         }

        //     }
        // }
    }

}