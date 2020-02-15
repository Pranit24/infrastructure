# AWS Cloudformation

## Create stack

```s
aws cloudformation create-stack \
  --stack-name csye6225demo \
  --parameters ParameterKey=KeyPair,ParameterValue=Value \
  --template-body file://networking.json --profile user
```

or

```s
aws cloudformation create-stack \
  --stack-name csye6225demo \
  --parameters file://networking_parameters.json \
  --template-body file://networking.json --profile user
```

## Parameters

- EnvironmentName \
  Environment name that is prefixed to resource names

- VpcCIDR \
  IP range(CIDR notation) for this VPC  
  Example

```
10.0.0.0/16
```

- Subnets\

  The subnets addresses should be within the VPC address \
  Example
```
10.0.0.0 to 10.0.255.255
```

 - PublicSubnet1CIDR\
   IP range (CIDR notation) for the public subnet in the first  Availability Zone
 
 - PublicSubnet2CIDR\
   IP range (CIDR notation) for the public subnet in the sceond  Availability Zone
 
 - PublicSubnet3CIDR\
   IP range (CIDR notation) for the public subnet in the third
 
 - AvailabilityZones \
   Comma delimited list of availability zones. MAX 3

JSON file for parameters

```javascript
[
  {
    ParameterKey: "EnvironmentName",
    ParameterValue: "Networking VPC"
  },
  {
    ParameterKey: "VpcCIDR",
    ParameterValue: "*.*.*.*/16"
  },
  {
    ParameterKey: "PublicSubnet1CIDR",
    ParameterValue: "*.*.*.*/24"
  },
  {
    ParameterKey: "PublicSubnet2CIDR",
    ParameterValue: "*.*.*.*/24"
  },
  {
    ParameterKey: "PublicSubnet3CIDR",
    ParameterValue: "*.*.*.*/24"
  },
  {
    ParameterKey: "AvailabilityZones",
    ParameterValue: "region_1,region_2,region_3"
  }
];
```
