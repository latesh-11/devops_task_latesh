def SANITIZED_BRANCH_NAME = env.BRANCH_NAME.toLowerCase().replaceAll("/", "-")
pipeline {
    agent any

    environment {
        APP_DIRECTORIES = ['GO_Application', 'Next_js_Application', 'Wordpress_Application']
        APP_IMAGES = ['go-app', 'next-app', 'wordpress-app']
        REGISTRY = 'https://746319289656.dkr.ecr.us-east-1.amazonaws.com/'
        CREDENTIALS = 'docker-hub-CREDENTIALS'
        BUILD  = "${APP_IMAGES[i]}:${SANITIZED_BRANCH_NAME}_${BUILD_NUMBER}"
        LATEST_BUILD = "${APP_IMAGES[i]}:latest"

    }

    stages {
        stage('Linting') {
            parallel {
                stage('GolangCI-Lint') {
                    steps {
                        dir('GO_Application') {
                            sh 'golangci-lint run'
                        }
                    }
                }
                stage('ESLint') {
                    steps {
                        dir('Next_js_Application') {
                            sh 'npx eslint .'
                        }
                    }
                }
                stage('PHPCS') {
                    steps {
                        dir('Wordpress_Application') {
                            sh 'vendor/bin/phpcs'
                        }
                    }
                }
            }
        }
        stage('Testing') {
            parallel {
                stage('Go Tests') {
                    steps {
                        dir('GO_Application') {
                            sh 'go test ./...'
                        }
                    }
                }
                stage('Jest') {
                    steps {
                        dir('Next_js_Application') {
                            sh 'npm test'
                        }
                    }
                }
                stage('PHPUnit') {
                    steps {
                        dir('Wordpress_Application') {
                            sh 'vendor/bin/phpunit'
                        }
                    }
                }
            }
        }
        stage('Image Build and Push') {
            steps {
                script {
                    for (int i = 0; i < APP_DIRECTORIES.size(); i++) {
                        dir("${APP_DIRECTORIES[i]}") {
                            if (env.BRANCH_NAME == "${DEV_REPO_BRANCH_NAME}") {
                                sh 'sudo chmod 666 /var/run/docker.sock'

                                docker.withREGISTRY("${REGISTRY}", "ecr:us-east-1:${CREDENTIALS}") {

                                    def image = docker.build("${REGISTRY}/${APP_IMAGES[i]}:${env.BUILD_NUMBER}")
                                    
                                    BUILD = docker.build("${ECR_BUILD}")
                                    BUILD.push()

                                    LATEST_BUILD = docker.build("${ECR_LATEST_BUILD}")
                                    LATEST_BUILD.push()
                                }
                            }
                        }
                    }
                }
            }
        }
        stage('Compose Build') {
            parallel {
                stage('Build Go App') {
                    steps {
                        dir('path/to/go-app') {
                            sh 'docker-compose -f docker-compose.go.yml build'
                        }
                    }
                }
                stage('Build Next.js App') {
                    steps {
                        dir('path/to/next-app') {
                            sh 'docker-compose -f docker-compose.next.yml build'
                        }
                    }
                }
                stage('Build WordPress App') {
                    steps {
                        dir('path/to/wordpress-app') {
                            sh 'docker-compose -f docker-compose.wordpress.yml build'
                        }
                    }
                }
            }
        }
    }
}
