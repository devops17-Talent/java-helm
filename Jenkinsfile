pipeline{
  agent any
  stages{
    stage('connecting to cluster'){
      steps{
      sh 'kubectl config use-context arn:aws:eks:us-west-2:897276212041:cluster/devops-eks-gCFGYxzJ'
      }
  }
    /*stage('create db namespace'){
      steps{
    sh '''
        myNamespace="database"
       kubectl get namespace | grep -q "^$myNamespace " || kubectl create namespace $myNamespace
         '''
    }
    }*/
  stage('deploy java'){
    steps{
    sh 'helm upgrade --install javaspring $WORKSPACE --values $WORKSPACE/values.yaml --namespace devops-java '
    }
  }
 stage('pod status'){
   steps{
   sh 'kubectl get pods -n devops-java'
   }
 }
    
}
}
