# CDKaaL - CDK as a Layer

This package will help you install CDK as a Lambda Layer. An example use-case for this is if you are using Lamdba as a mechanism to deploy your applications.

# How to install

Here's a couple easy options for you:

## 1. Install Layer using ARN:

Go to your Lambda and click `Add a Layer`

```
arn:aws:lambda:us-east-1:588317532452:layer:CDKaaL:1
```

![LayerUsingARN](https://github.com/campionfellin/CDKaaL/raw/master/images/LayerUsingARN.png)

> Note: the layer is built using `nodejs12.x` and is in `us-east-`. If you need another version or region, please open an issue and I can update this.

> Note: this is on version 1, and last updated on 02/02/2020

## 2. Zip and Install Layer Yourself

```
git clone https://github.com/campionfellin/CDKaaL.git
cd CDKaal/nodejs
npm i
cd ..
zip -r nodejs.zip nodejs
```

Then go to Lamba layers and upload `nodejs.zip` as your source code.

![LayerUsingZIP](https://github.com/campionfellin/CDKaaL/raw/master/images/LayerUsingZIP.png)

# How to use

This layer can be used in 2 ways:

## 1. As a standard dependency:

In your Lambda's code, you can use

```
import cdk = require('@aws-cdk/core');
```

as you normally would, without needing to upload the entire `aws-cdk` node module as part of your Lambda deployment.  Right now the *zipped* size of `aws-cdk` is ~15mb and the *unzipped* size is ~70mb.

## 2. As a CLI:

This will also install the AWS-CDK CLI at `/opt/nodejs/cdk` so you can deploy CDK apps with your Lambda.

Example usage in a NodeJS Lambda:

```
const { exec } = require('child_process');

exec(`/opt/nodejs/cdk --version`, (err, stdout, stderr) => {
  .
  .
  .    
});
```
