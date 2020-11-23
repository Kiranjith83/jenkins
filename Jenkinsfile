
pipeline {
    agent any
    parameters {
          string(name: 'AWS_DEFAULT_REGION', defaultValue: 'ap-southeast-2', description: 'The region to deploy to')
    }
    stages {
      stage('Test') {
        agent any
        steps {
          sh '''#!/usr/bin/env bash
          aws sts get-caller-identity
          '''
        }
      }
      stage('Create CloudFormation Package from Serverless code') {
        steps {
          sh '''echo "aws cloudformation package --template-file master-template.yaml --s3-bucket <bucket name> --output-template-file cfn-template.yaml"
          '''
          sh '''echo "Hellow world 2"
          '''
          sh '''
          echo "Hellow world 3" '''
        }
      }
  
      stage('Deploy the CFN package') {
        steps {
          sh '''echo "aws cloudformation deploy --template-file cfn-template.yaml --stack-name master-automation --parameter-overrides Key1=Value1 Key2=Value2"'''
          sh '''#!/usr/bin/env bash
         echo "Hello world from Deploy stage"
         '''
        }
      }
    }
  }