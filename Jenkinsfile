pipeline {
agent any
    stages {
        stage ('skript') {
            steps {
                script {
                    sh "rm -r Mikolaskript"
                    sh "git clone https://github.com/vadimchodakowski/Mikolaskript.git"
                    dir('Mikolaskript') {
                    sh "ls -la && pwd"
                    def mylambdas = sh(script: """ls -d */ | tr -d / | grep -v 'jenkins'""", returnStdout: true).trim()
                        def arroflambdas=[]
                            mylambdas.split().each { 
                                arroflambdas << it
                            }
                    echo "${mylambdas}"
                        for (int i = 0; i < arroflambdas.size(); i++) {
                            def pathTocodebase = "${arroflambdas[i]}"
                                dir(pathTocodebase) {
                                    sh "ls -la && pwd"
                                    echo "${arroflambdas[i]}"
                                    echo "deploying ${arroflambdas[i]}"
                                    sh "chmod 777 ./skript.sh"
                                    sh "./skript.sh"
                            }
                        }
                    }
                }
            }
        }
    }
}