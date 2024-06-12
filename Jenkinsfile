pipeline {
    agent any

    parameters {
        string(name: 'MAVEN_VERSION', defaultValue: '3.8.6', description: 'Version of Maven to download')
        string(name: 'TERRAFORM_VERSION', defaultValue: '1.2.5', description: 'Version of Terraform to download')
    }

    
        stage('Download Terraform') {
            steps {
                script {
                    sh '''
                        echo "Changing directory to ${WORKSPACE}"
                        cd ${WORKSPACE}

                        echo "Downloading Terraform version ${TERRAFORM_VERSION}"
                        wget -q https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip -O terraform_${TERRAFORM_VERSION}_linux_amd64.zip

                        echo "Extracting Terraform"
                        unzip -o terraform_${TERRAFORM_VERSION}_linux_amd64.zip
                        rm terraform_${TERRAFORM_VERSION}_linux_amd64.zip
                    '''
                }
            }
        }
    }
}
