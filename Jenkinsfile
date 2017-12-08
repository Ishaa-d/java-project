node('linux'){
stage('UnitTests'){

   sh 'ant'

   sh 'ant -f test.xml -v'

   junit 'reports/result.xml'

}

stage('Build'){

   sh 'ant -f build.xml -v'

}

stage('Deploy'){
   sh 'aws s3 cp *.jar jenkins-stack-s3bucket-1lni2dkquioa6.s3.amazonaws'
}
stage('Report'){
    stage ('UnitTests'){
        withCredentials([[$class: 'AmazonWebServicesCredentialsBinding', accessKeyVariable: 'AWS_ACCESS_KEY_ID', credentialsId: 'dd9e4120-ca1c-4fe1-8008-16b6993948c7', secretKeyVariable: 'AWS_SECRET_ACCESS_KEY']]){
            sh 'aws cloudformation describe-stack-resources --region us-east-1 --stack-name jenkins'
}
}
}
}
