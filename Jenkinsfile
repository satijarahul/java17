node {

    try {

       stage('Checkout Code')
       {
          checkout scm
       }
    

       stage('Build Code')
       {
       	  withMaven(traceability: true,maven:'Maven_HOME' ,jdk:'jdk'){
             bat 'mvn clean package -Dmaven.test.skip=true'
         }

       }
        stage('Run Unit Tests')
         {
			withMaven(traceability: true,maven:'Maven_HOME' , jdk:'jdk'){
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