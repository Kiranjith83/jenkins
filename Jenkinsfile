pipeline {
    agent any
    parameters {
          string(name: 'aws_region', defaultValue: 'ap-southeast-2', description: 'The region to deploy CFN Stack')
          string(name: 's3_artifact', defaultValue: 's3artifactbucket', description: 'The region to deploy CFN Stack')
          string(name: 'stack_name', defaultValue: 'sec-automation', description: 'The region to deploy CFN Stack')         
    }
    stages {
      stage('Test') {
        agent any
        steps {
          sh '''#!/usr/bin/env bash
          echo "Emitting current aws creds to work log"
          aws sts get-caller-identity
          '''
        }
      }
      stage('Create CloudFormation Package from Serverless code') {
        steps {
          echo "aws cloudformation package --template-file master-template.yaml --s3-bucket  ${params.s3_artifact} --output-template-file cfn-template.yaml"
        }
      }
  
      stage('Deploy the CFN package') {
        steps {
          echo "aws cloudformation deploy --template-file cfn-template.yaml --stack-name ${params.stack_name} --parameter-overrides Key1=Value1 Key2=Value2 --region ${params.aws_region}"
        }
      }
    }
  }