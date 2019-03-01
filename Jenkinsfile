node {
    stage('Checkout') {
        checkout([$class: 'GitSCM', branches: [[name: '*/$branch']], 
            doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], 
            userRemoteConfigs: [[credentialsId:'/$githubToken' , url: 'git@github.com:pablojotaguardiola/test-jenk.git']]])
    }
    stage('Clean') {
        sh 'fastlane clean_xcode'
    }
    stage('Code Sign') {
        sh 'fastlane codesign method:"adhoc"'
    }
    stage('Create Build') {   
        sh 'fastlane create_build'
    }
}