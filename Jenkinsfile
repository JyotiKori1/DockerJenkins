pipeline {
    agent any
    stages {
        stage('Build Jar') {
  //          agent {
  //             docker {
   //                image 'maven:3-alpine'
     //               args '-v $HOME/.m2:/root/.m2'
      //          }
      //     }
            steps {
                //sh 
                bat 'mvn clean package -DskipTests'
            }
        }
       stage('Build Image') {
        steps {
		step {
             app = docker.build("jyotikori/selenium-docker")
		}
           }
        }
        stage('Push Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable:'pass',usernameVariable:'user')])
			        //docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
			        //	app.push("${BUILD_NUMBER}")
			        //    app.push("latest")
			        bat "docker login --username=${user} --password=${pass}"
			        echo "docker login completed"
			        bat "docker push JyotiKori/selenium-docker:latest"
			        echo "docker push completed"
			    
                }
            }
        }
    }
