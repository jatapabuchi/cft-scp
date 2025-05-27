{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Sid": "RequireMandatoryTagsOnec2Creation",
      "Effect": "Deny",
      "Action": [
        "ec2:RunInstances",
        "ec2:CreateVolume",
        "ec2:CreateNetworkInterface"
      ],
      "Resource": [
        "arn:aws:ec2:*:*:instance/*",
        "arn:aws:ec2:*:*:volume/*",
        "arn:aws:ec2:*:*:network-interface/*"
      ],
      "Condition": {
        "Null": {
          "aws:RequestTag/Owner": "true"
        }
      }
    },
    {
      "Sid": "DenyResourceCreationWithoutOwnerTag",
      "Effect": "Deny",
      "Action": [
        "rds:CreateDBInstance",
        "rds:CreateDBCluster",
        "elasticache:CreateCacheCluster",
        "elasticache:CreateServerlessCache",
        "elasticloadbalancing:CreateLoadBalancer",
        "elasticloadbalancing:CreateTargetGroup",
        "fsx:CreateFileSystem",
        "ecs:CreateCluster",
        "ecs:CreateService",
        "eks:CreateCluster",
        "elasticbeanstalk:CreateApplication",
        "elasticbeanstalk:CreateEnvironment",
        "dynamodb:CreateTable",
        "backup:CreateBackupPlan",
        "athena:CreateWorkGroup",
        "glue:CreateJob",
        "sns:CreateTopic",
        "sqs:CreateQueue",
        "secretsmanager:CreateSecret",
        "acm:RequestCertificate",
        "kinesis:CreateStream",
        "kms:CreateKey",
        "batch:CreateComputeEnvironment",
        "batch:CreateJobQueue",
        "directconnect:CreateConnection",
        "elasticfilesystem:CreateFileSystem"
      ],
      "Resource": "*",
      "Condition": {
        "Null": {
          "aws:RequestTag/Owner": "true"
        }
      }
    }
  ]
}
