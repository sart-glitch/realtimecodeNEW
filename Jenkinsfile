pipeline{
     
    tools{
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
       }
      
     agent any
        stages{
            stage('clone repo'){
           
            steps{
                git credentialsId: '26dedd60-8aee-4f52-a544-b68ee82c607f', url: 'https://github.com/ashisnishanka/realtimecodeNEW.git'
		    
                }
				}
             stage('Compile'){
                agent any
                  
                steps{
                    git credentialsId: '26dedd60-8aee-4f52-a544-b68ee82c607f', url: 'https://github.com/ashisnishanka/realtimecodeNEW.git'
                    sh 'mvn compile'
                }
                
            }
            stage('CodeReview'){
               
                steps{
                    git credentialsId: '26dedd60-8aee-4f52-a544-b68ee82c607f', url: 'https://github.com/ashisnishanka/realtimecodeNEW.git'
                    sh 'mvn pmd:pmd'
                }
                post{
                    always{
                        //dependencyCheckPublisher pattern: 'target/pmd.xml'
                           //pmd pattern: 'target/pmd.xml'
                          // maven.pmd.rulesetfiles
                          echo 'postbuild action successfully '
                   }
                }
            }
            stage('UnitTest'){
                //agent {label 'mywinjob'}
                       
                steps{
                  
                   //git 'give git url'
                   git credentialsId: '26dedd60-8aee-4f52-a544-b68ee82c607f', url: 'https://github.com/ashisnishanka/realtimecodeNEW.git'
                    sh 'mvn test'
                }
                
            }
            stage('MetriCheck'){
                
                steps{
                    git credentialsId: '26dedd60-8aee-4f52-a544-b68ee82c607f', url: 'https://github.com/ashisnishanka/realtimecodeNEW.git'
                    sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
                }
                post{
                    always{
                        cobertura coberturaReportFile: 'target/site/cobertura/coverage.xml'
                    }
                }
            }
            stage('Package'){
                
                steps{
                    git credentialsId: '26dedd60-8aee-4f52-a544-b68ee82c607f', url: 'https://github.com/ashisnishanka/realtimecodeNEW.git'
                    sh 'mvn package'
                }
            }
		stage(' QA deploy'){
                
                steps{
                    //git credentialsId: '26dedd60-8aee-4f52-a544-b68ee82c607f', url: 'https://github.com/ashisnishanka/realtimecodeNEW.git'
                    //sh 'mvn package'
			echo " QA deploy the application"
                }
            }
			
		stage(' dev deploy'){
                
                steps{
                    //git credentialsId: '26dedd60-8aee-4f52-a544-b68ee82c607f', url: 'https://github.com/ashisnishanka/realtimecodeNEW.git'
                    //sh 'mvn package'
			echo "dev deploy the application"
                }
            }
            
        }
    
    }
