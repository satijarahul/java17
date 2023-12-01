node {

    try {

       stage('Checkout Code')
       {
          checkout scm
       }
    

       stage('Build Code')
       {
           bat 'C:\Program Files\apache-maven-3.9.5\bin\mvn clean package -Dmaven.test.skip=true'
       }
        stage('Run Unit Tests')
         {
			    bat 'C:\Program Files\apache-maven-3.9.5\bin\mvn test'
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