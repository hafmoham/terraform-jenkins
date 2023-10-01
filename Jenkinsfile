pipeline{
  agent any
  environment {
    PATH = "${PATH}:${getTerraformPath()}"
  }
  stages{
    stage('S3 - create bucket'){
      steps{
        echo "S3 - create bucket"
      }
    }
    stage('terraform init and apply - dev'){
      steps{
        sh returnStatus: true, script: 'terraform workspace new dev'
        sh "terraform init"
        echo "terraform init and apply - dev"
      }
    }

    stage('terraform init and apply - prod'){
      steps{
        sh returnStatus: true, script: 'terraform workspace new prod'
        sh "terraform init"
         echo "terraform init and apply - prod"
      }
    }
  }
}

def getTerraformPath(){
  def tfHome = tool name: 'terraform-12', type: 'org.jenkinsci.plugins.terraform.TerraformInstallation'
  return tfHome
}
