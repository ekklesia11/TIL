1. Create IAM role for code deploy and ec2

create role EC2 > select policy AmazonEC2RoleforAWSCodeDeploy

click on it -> select Add inline policy->click json tab



코드디플로이를 설치할 때 bucket-name 에 들어가야 하는건 aws-codedeploy-[region] 이다. => Resource Kit Bucket Names by Region 참조

wget https://aws-codedeploy-ap-northeast-2.s3.ap-northeast-2.amazonaws.com/latest/install

