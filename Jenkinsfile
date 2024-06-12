pipeline {
    agent any

    parameters {
        string(name: 'MAVEN_VERSION', defaultValue: '3.8.6', description: 'Version of Maven to download')
        string(name: 'TERRAFORM_VERSION', defaultValue: '1.2.5', description: 'Version of Terraform to download')
    }

    stages {
        stage('Download Maven') {
            steps {
                script {
                    sh '''
                        echo "Changing directory to ${WORKSPACE}"
                        cd ${WORKSPACE}

                        echo "Downloading Maven version ${MAVEN_VERSION}"
                        wget -q https://dlcdn.apache.org/maven/maven-3/${MAVEN_VERSION}/binaries/apache-maven-${MAVEN_VERSION}-bin.tar.gz -O apache-maven-${MAVEN_VERSION}-bin.tar.gz

                        echo "Extracting Maven"
                        tar -xzf apache-maven-${MAVEN_VERSION}-bin.tar.gz
                        rm apache-maven-${MAVEN_VERSION}-bin.tar.gz
                    '''
                }
            }
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
