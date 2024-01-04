pipeline {
    agent any
    
    stages {
        stage('Checkout SCM') {
            steps {
                script {
                    // Your SCM checkout steps here
                    // For example, Git checkout
                    checkout scm
                }
            }
        }

        stage('Deploy PHP Application') {
            steps {
                script {
                    // Your deployment steps here
                    sshPublisher(
                        publishers: [
                            sshPublisherDesc(
                                configName: 'apache2',
                                transfers: [
                                    sshTransfer(
                                        execCommand: 'Deploy PHP application',
                                        execTimeout: 120000,
                                        sourceFiles: '**/*.php',
                                        remoteDirectory: '/var/www/html',
                                        keyPath: '/home/ubuntu/.ssh',  
                                        cleanRemote: false
                                    )
                                ]
                            )
                        ]
                    )
                }
            }
        }
    }
}
