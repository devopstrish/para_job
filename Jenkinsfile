pipeline {
    agent any

    parameters {
        string(name: 'MAVEN_VERSION', defaultValue: '3.8.6', description: 'Version of Maven to download')
        string(name: 'TERRAFORM_VERSION', defaultValue: '1.2.5', description: 'Version of Terraform to download')
    }

    environment {
        MAVEN_URL = "https://downloads.apache.org/maven/maven-3/${params.MAVEN_VERSION}/binaries/apache-maven-${params.MAVEN_VERSION}-bin.tar.gz"
        MAVEN_HOME = "${env.WORKSPACE}/maven"

        TERRAFORM_URL = "https://releases.hashicorp.com/terraform/${params.TERRAFORM_VERSION}/terraform_${params.TERRAFORM_VERSION}_linux_amd64.zip"
        TERRAFORM_HOME = "${env.WORKSPACE}/terraform"
    }

    stages {
        stage('Download Maven') {
            steps {
                script {
                    // Download Maven
                    sh """
                        echo "Downloading Maven version ${params.MAVEN_VERSION}"
                        curl -s -o maven.tar.gz ${MAVEN_URL}
                        tar -xzf maven.tar.gz
                        mv apache-maven-${params.MAVEN_VERSION} ${MAVEN_HOME}
                        rm maven.tar.gz
                    """
                }
            }
        }

        stage('Download Terraform') {
            steps {
                script {
                    // Download Terraform
                    sh """
                        echo "Downloading Terraform version ${params.TERRAFORM_VERSION}"
                        curl -s -o terraform.zip ${TERRAFORM_URL}
                        unzip terraform.zip -d ${TERRAFORM_HOME}
                        rm terraform.zip
                    """
                }
            }
        }

    }
}
