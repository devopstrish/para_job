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
                        echo "Downloading Maven version ${MAVEN_VERSION}"
                        sudo wget -q https://dlcdn.apache.org/maven/maven-3/${MAVEN_VERSION}/binaries/apache-maven-${MAVEN_VERSION}-bin.tar.gz -O /tmp/maven.tar.gz
                        if file /tmp/maven.tar.gz | grep -q gzip; then
                            sudo mkdir -p /opt/maven
                            sudo tar -xzf /tmp/maven.tar.gz -C /opt/maven --strip-components=1
                            sudo rm /tmp/maven.tar.gz
                        else
                            echo "Downloaded file is not a valid gzip archive"
                            exit 1
                        fi
                    '''
                }
            }
        }

        stage('Download Terraform') {
            steps {
                script {
                    sh '''
                        echo "Downloading Terraform version ${TERRAFORM_VERSION}"
                        sudo wget -q https://releases.hashicorp.com/terraform/${TERRAFORM_VERSION}/terraform_${TERRAFORM_VERSION}_linux_amd64.zip -O /tmp/terraform.zip
                        if file /tmp/terraform.zip | grep -q 'Zip archive data'; then
                            sudo mkdir -p /opt/terraform
                            sudo unzip /tmp/terraform.zip -d /opt/terraform
                            sudo rm /tmp/terraform.zip
                        else
                            echo "Downloaded file is not a valid zip archive"
                            exit 1
                        fi
                    '''
                }
            }
        }

        stage('Verify Installation') {
            steps {
                script {
                    sh '''
                        echo "Verifying Maven installation"
                        /opt/maven/bin/mvn -version

                        echo "Verifying Terraform installation"
                        /opt/terraform/terraform -version
                    '''
                }
            }
        }
    }
}
