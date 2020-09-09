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
   //     stage('Build Image') {
   //         steps {
    //            script {
     //           	app = docker.build("jyotikori/selenium-docker")
       //         }
       //     }
      //  }
        stage('Push Image') {
            steps {
                withCredentials([usernamePassword(credentialsId: 'dockerhub', passwordVariable:'pass',usernamVariable:'user')])
			        //docker.withRegistry('https://registry.hub.docker.com', 'dockerhub') {
			        //	app.push("${BUILD_NUMBER}")
			        //    app.push("latest")
			        bat "docker login --username=${user} --password=${pass}"
			        bat "docker push JyotiKori/selenium-docker:latest"
			    
                }
            }
        }
    }

