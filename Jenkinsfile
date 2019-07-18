pipeline {
    agent { label 'MASTER' }
        parameters {
            string(defaultValue: "/Users/jenkins/.jenkins/jobs", description: 'Path to Jenkins Jobs', name: 'FILES_PATH')
            string(defaultValue: "4w", description: 'EXAMPLE: 4w 3d etc', name: 'FILES_AGE')
            string(defaultValue: "100m", description: 'EXAMPLE: 100m 2000m', name: 'FILES_SIZE')      
    }
    stages {
        //stage('Cleanup Jenkins Job Workspace'){
            //steps {
                //step([$class: 'WsCleanup'])
            //}
        //}       
        stage('Run Ansible Query operation'){        
            steps {            
            wrap([$class: 'AnsiColorBuildWrapper', colorMapName: "xterm"]) {
                    echo 'Validate Access'
                    ansiblePlaybook credentialsId: 'jenkins',
                    installation: 'ansible', 
                        inventory: '/Users/${MY_USERID}/macos_inventory',
                    limit: 'all',
                        playbook: '${WORKSPACE}/ansible_macos.yml',
                    colorized: false
                }
            }
        }
        stage('Demo Performance'){
            steps {
                echo 'Clap if you liked the demo!'
            }
        }

    }
}