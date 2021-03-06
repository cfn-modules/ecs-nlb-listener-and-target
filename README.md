# cfn-modules: ECS NLB listener and target

ECS NLB listener and target.

## Install

> Install [Node.js and npm](https://nodejs.org/) first!

```
npm i @cfn-modules/ecs-nlb-listener-and-target
```

## Usage

```
---
AWSTemplateFormatVersion: '2010-09-09'
Description: 'cfn-modules example'
Resources:
  Target:
    Type: 'AWS::CloudFormation::Stack'
    Properties:
      Parameters:
        NlbModule: !GetAtt 'Nlb.Outputs.StackName' # required
        VpcModule: !GetAtt 'Vpc.Outputs.StackName' # required
        Port: '80' # optional
        CertificateArn: '' # optional
        ClientSgModule: '' # optional
        DeregistrationDelayInSeconds: '60' # optional
        Protocol: 'TCP' # optional
      TemplateURL: './node_modules/@cfn-modules/ecs-nlb-listener-and-target/module.yml'
```

## Examples

none

## Related modules

* [nlb](https://github.com/cfn-modules/nlb)

## Parameters

<table>
  <thead>
    <tr>
      <th>Name</th>
      <th>Description</th>
      <th>Default</th>
      <th>Required?</th>
      <th>Allowed values</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>NlbModule</td>
      <td>Stack name of <a href="https://www.npmjs.com/package/@cfn-modules/nlb">nlb module</a></td>
      <td></td>
      <td>yes</td>
      <td></td>
    </tr>
    <tr>
      <td>VpcModule</td>
      <td>Stack name of <a href="https://www.npmjs.com/package/@cfn-modules/vpc">vpc module</a></td>
      <td></td>
      <td>yes</td>
      <td></td>
    </tr>
    <tr>
      <td>Port</td>
      <td>The port on which the listener listens for requests</td>
      <td>80</td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>CertificateArn</td>
      <td>Amazon Resource Name (ARN) of the certificate to associate with the listener</td>
      <td></td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>ClientSgModule</td>
      <td>Stack name of <a href="https://www.npmjs.com/package/@cfn-modules/client-sg">client-sg module</a> where traffic is allowed from on port $Port to the listener (requires NLB Scheme := internal)</td>
      <td></td>
      <td>no</td>
      <td></td>
    </tr>
    <tr>
      <td>DeregistrationDelayInSeconds</td>
      <td>The amount of time, in seconds, for Elastic Load Balancing to wait before changing the state of a deregistering target from draining to unused</td>
      <td>60</td>
      <td>no</td>
      <td>0-3600</td>
    </tr>
    <tr>
      <td>Protocol</td>
      <td>The protocol for connections from clients to the load balancer.</td>
      <td>TCP</td>
      <td>no</td>
      <td>[TCP, UDP, TCP_UDP]</td>
    </tr>
  </tbody>
</table>
