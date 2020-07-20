pipeline {
  agent any
  tools {
    jdk 'jdk1.8'
    maven 'maven3'
  }
  stages{
    stage('git pull'){
      steps{
         echo 'this stage is for pull repo'
	 git 'https://github.com/giricse/ans_roles_demo.git'
      }
    }
    stage('mvn install'){
      steps{
	echo ' maven clean & install'
	sh 'mvn clean'
	sh 'mvn install'
      }
    }
	stage('ansible slave ping check'){
      steps{
       echo 'ping check to slave'
       sh 'ansible tag_Name_slave -m ping'
      }
    }
    stage('ansible role syntax check'){
      steps{
       echo 'ansible role syntax check'
       sh 'ansible-playbook run.yml --syntax-check'
      }
    }
    stage('ansible role execution'){
	    steps{
		    echo 'Executing roles'
		    sh 'ansible-playbook run.yml'
}
    }
  }
}
