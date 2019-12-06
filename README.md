# Renewable Energy Forecasts via Cornell EAS Data Lake

## https://registry.opendata.aws/cornell-eas-data-lake/

Using the NOAA National Digital Forecast Database (NDFD), provided via the Cornell EAS Convenience Data Lake, we can make a high-resolution forecast animation of sky cover and wind speed for any region in the Contiguous US.

This visual can be used to supplement predictions for the general energy output of solar and wind farms. 

## How to:

1. All you need is the AWS CLI installed and your AWS Account Credentials with Administrator Access configured via environment variables

2. Take a look at the `config.sh` file to change between `sky` or `wspd` predictions, to change the coordinates/area of your map, or to change the timezone for the map timestamps

3. Run the `./forecast` script to deploy the serverless resources to your AWS Account and monitor the progress

4. Examine the generated animation provided at the link in the output

## What is happening:

1. Serverless resources are deployed to your AWS Account via CloudFormation

2. AWS CodeBuild installs dependencies and deploys a Python Lambda Function

3. AWS Step Functions runs a State Machine that produces an NDFD Forecast Animation

4. Amazon Athena is used to query the latest NDFD forecast via the Cornell EAS Convenience Data Lake

5. Python is used to consume the query results and produce a GIF forecast animation using Cartopy and Matplotlib 
