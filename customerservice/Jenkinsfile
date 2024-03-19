node {
    stage ("Checkout CustomerServiceAPI"){
        git branch: 'main', url: ' https://github.com/foxwas/customerserviceAPI.git'
    }
    
    stage ("Maven Build - CustomerServiceAPI") {
	
        bat 'mvn install -DskipTests'

    }
	
	stage ("Launch the App - CustomerServiceAPI") {
	
        bat 'start mvn spring-boot:run'
		
    }
	
    
    stage ("API Tests- CustomerServiceAPI") {
        bat  'mvn test'
    }
    
    stage('User Acceptance Test - CustomerServiceAPI') {
	
	  def response= input message: 'Is this build good to go?',
	   parameters: [choice(choices: 'Yes\nNo', 
	   description: '', name: 'Pass')]
	
	  if(response=="Yes") {

	    stage('Release- Customer Service API') {
	     bat 'echo Customer Service API is ready to release!'
		 bat 'echo release team may create a docker container image'

	    }
	  }
    }
}