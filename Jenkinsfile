node{
     
    stage('SCM Checkout'){
        git credentialsId: 'GIT_CREDENTIALS', url:  'https://github.com/acadalearning/Jenkins-Docker-K8s-Spring-boot-mongo.git',branch: 'master'
    }
   
    stage(" Maven Clean Package"){
      def mavenHome =  tool name: "Maven-3.8.5", type: "maven"
      def mavenCMD = "${mavenHome}/bin/mvn"
      sh "${mavenCMD} clean package"
      
    } 
    stage('Build Docker Image'){
        sh 'docker build -t acadalearning/spring-boot-mongo .'
    }
    
    
    stage('Build Docker Image'){
        sh 'docker build -t acadalearning/spring-boot-mongo .'
    }
    // some block

    stage('Push Docker Image'){
          //withCredentials([usernameColonPassword(credentialsId: 'dockerhub', variable: 'password')]) {
          sh "docker login -u idowudevops -p Windyspark77!
        }
        sh 'docker push idowudevops/spring-boot-mongo'
     }
     
     stage("Deploy To Kuberates Cluster"){
       kubernetesDeploy(
         configs: 'springBootMongo.yml', 
         kubeconfigId: 'KUBERNATES_CONFIG',
         enableConfigSubstitution: true
        )
     }
	 
	  /**
      stage("Deploy To Kuberates Cluster"){
        sh 'kubectl apply -f springBootMongo.yml'
      } **/
     
}
