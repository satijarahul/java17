node {

    try {

       stage('Checkout Code')
       {
          checkout scm
       }
    

       stage('Build Code')
       {
       	 dir("."){
             bat 'mvn clean package -Dmaven.test.skip=true'
         }

       }
        stage('Run Unit Tests')
         {
			dir("."){
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
 			sh 'echo "Build Failed"'
        }
        else 
        { 
        	sh 'echo "Build Success"'
        }
    }
}