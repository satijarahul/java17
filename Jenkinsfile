node {

    try {

       stage('Checkout Code')
       {
          checkout scm
       }
    

       stage('Build Code')
       {
       	  withMaven(traceability: true){
             bat 'mvn clean package -Dmaven.test.skip=true'
         }

       }
        stage('Run Unit Tests')
         {
			withMaven(traceability: true){
			    bat 'mvn test'
            }
        }
    }

    catch (err) {
        currentBuild.result = "FAILURE"
        throw err
    }

    finally
    {
        if (currentBuild.result == "FAILURE")
        {
 			bat 'echo "Build Failed"'
        }
        else 
        { 
        	bat 'echo "Build Success"'
        }
    }
}