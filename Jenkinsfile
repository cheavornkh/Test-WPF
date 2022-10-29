pipeline {
  
  agent any

  environment {
    MSBUILD = "C:\\Program Files (x86)\\Microsoft Visual Studio\\2019\\Community\\MSBuild\\Current\\Bin\\MSBuild.exe"
    CONFIG = 'Release'
    PLATFORM = 'x64'
  }
  
  stages {
    
    stage('Build Test WPF') {
      steps {
        bat "\"${MSBUILD}\" \"Test WPF\\Test WPF.sln\" /p:Configuration=${env.CONFIG} /p:AppxBundlePlatforms=${env.PLATFORM}"
      
      }
    }
	
	stage('Delete Files') {
      steps {
        bat "del /q \"Test WPF\\Test WPF\\bin\\x64\\Release\\*pdb\""
		bat "del /q \"Test WPF\\Test WPF\\bin\\x64\\Release\\*application\""
      }
    }
	
	stage('Copy Files') {
      steps {
        bat "xcopy /s \"Test WPF\\Test WPF\\bin\\x64\\Release\" Outputs"
      }
    }
	
  }
}