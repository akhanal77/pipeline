node('node2') {
    stage('Checkout'){
        git "https://github.com/akhanal77/pipeline.git"
        
        }
    stage('Compile'){
        def mvnHome = tool 'm3'
        dir('maventdd') {
        sh "'${mvnHome}/bin/mvn' clean compile"
        }
    }
    stage('Testing'){
        def mvnHome = tool 'm3'
        dir('maventdd') {
        sh "'${mvnHome}/bin/mvn' test"
        }
    }    
    stage('Integration Test'){
        dir('maventdd') {
        def mvnHome = tool 'm3'
        sh "'${mvnHome}/bin/mvn' package"
        }
    }
        stage('Deployment') {
            def mvnHome = tool 'm3'
            if(env.BRANCH_NAME !="master"){
                echo 'No Deployment'
            }
                else {
                    dir('maventdd'){
                    sh "'${mvnHome}/bin/mvn' install"
    			}
        }
    }

}
