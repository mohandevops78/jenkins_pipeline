
pipeline {

    agent any
  
    tools {
        maven 'mvn'
    }
    
   parameters {
    gitParameter branchFilter: 'origin/(.*)', defaultValue: 'master', name: 'BRANCH', type: 'PT_BRANCH'
  }

    stages {
        stage('Code Clone') {
            steps {
                echo 'Cloning the Code Here'
                git branch: "${params.BRANCH}", credentialsId: 'mohan_git', url: 'https://github.com/mohandevops78/mvn-project.git'
                sleep 10
            }
        }

        stage('Code Build') {
            steps {
                echo 'Building Code Here'
                sleep 10
                sh 'mvn clean install'
            }
        }

        stage('Code Test') {
            steps {
                echo 'Testing Code Here'
                sleep 10
                sh 'mvn test'
            }
        }

        stage('Code Store-Artifect') {
            steps {
                echo 'Storing Artifect here'
                sleep 10
                archiveArtifacts artifacts: '**/*.jar', followSymlinks: false
            }
        }
}

}



// CI   :  CODE CLONE  >  BUILD > TEST > STORE-Artifect 
