node {

    try {

       stage('Checkout Code')
       {
          checkout scm
       }
    

       stage('Build Code')
       {
           bat 'mvn clean package -Dmaven.test.skip=true'
       }
        stage('Run Unit Tests')
         {
			    bat 'mvn test'
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