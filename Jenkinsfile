pipeline{
    tools{
        jdk 'JAVA_HOME'
        maven 'M2_HOME'
    }
    agent any
        stages{
		stage("checkout"){
	   steps{
	   git 'https://github.com/ashisnishanka/realtimecodeNEW.git'
	   }
	   }
             stage('Compile'){
                agent any
                steps{
                    sh 'mvn compile'
                }
                
            }
            stage('CodeReview'){
                agent any
                steps{
                    sh 'mvn pmd:pmd'
                }
                
            }
            stage('UnitTest'){
                agent any
                steps{
                  
                    sh 'mvn test'
                }
                
            }
            stage('MetriCheck'){
                agent any
                steps{
                    sh 'mvn cobertura:cobertura -Dcobertura.report.format=xml'
                }
                
            }
            stage('Package'){
                agent any
                steps{
                    sh 'mvn package'
                }
            }
            
        }
    
    }
