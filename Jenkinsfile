pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        // Checkout your source code from version control
        checkout scmGit(branches: [[name: '*/master']], extensions: [], userRemoteConfigs: [[credentialsId: 'github-cmake.', url: 'https://github.com/kvsubrahmanyam/cmakesample.git']])
        
        // Set up CMake environment
        withEnv(["PATH+CMK=${tool 'cmake'}/bin"]) {
          sh 'cmake -Bbuild -H.'
        }
      }
    }
    
    stage('Compile') {
      steps {
        // Build the project
        dir('build') {
          sh 'cmake --build .'
        }
      }
    }
    
    // Add more stages for testing, packaging, deployment, etc.
  }
}
