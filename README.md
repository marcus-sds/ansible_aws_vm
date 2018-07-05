# ansible_aws_vm

## login to ansible installed container or install ansible

- login to ansible container

    - install docker
   
    - docker pull

- install anisble manually

        $ virtualenv ansible
        $ source ansible/bin/activate

        $ pip install --upgarde setuptools pip
        $ pip install ansible

        or 
        $ pip install -r requirements.txt

        (ansible)ubuntu@ip-10-10-32-74:~$ cat requirements.txt
        ansible==2.4.2.0
        asn1crypto==0.24.0
        bcrypt==3.1.4
        boto==2.48.0
        cffi==1.11.2
        cryptography==2.1.4
        enum34==1.1.6
        idna==2.6
        ipaddress==1.0.19
        Jinja2==2.10
        MarkupSafe==1.0
        paramiko==2.4.0
        pyasn1==0.4.2
        pycparser==2.18
        PyNaCl==1.2.1
        PyYAML==3.12
        six==1.11.0

## Creating Several vms with AWS

### Procedure

- clone repository

        git clone https://github.com/marcus-sds/ansible_aws_vm.git
        cd ansible_aws_vm

- change value

        vi ./group_vars/all.yml
        vi aws_ec2.yml

- run script

        bash ./example

## spot instance price

### aws_ec2.yml file includes **spot_price: 0.05**. User can edit the instance type and spot bidding price.

| No               | Region         | Family            | Type        | Cost ($/hour) | Cost ($/month) | Spot ($/hour) | Spot ($/month)  |     |     | 
|------------------|----------------|-------------------|-------------|---------------|----------------|---------------|-----------------|-----|-----| 
| (ondemand ratio) | CPU            | Memory            |             |               |                |               |                 |     |     | 
| 1                | ap-northeast-2 | General purpose   | t2.nano     | 0.0072        | 5.26           | NA            | NA (%)          | 1   | 1   | 
| 2                | ap-northeast-2 | General purpose   | t2.micro    | 0.0144        | 10.51          | 0.0043        | 3.14 (30%)      | 1   | 1   | 
| 3                | ap-northeast-2 | General purpose   | t2.small    | 0.0288        | 21.02          | 0.0086        | 6.28 (30%)      | 1   | 2   | 
| 4                | ap-northeast-2 | General purpose   | t2.medium   | 0.0576        | 42.05          | 0.0173        | 12.63 (30%)     | 2   | 4   | 
| 5                | ap-northeast-2 | Compute optimized | c5.large    | 0.096         | 70.08          | 0.028         | 20.44 (29%)     | 2   | 4   | 
| 6                | ap-northeast-2 | Compute optimized | c4.large    | 0.114         | 83.22          | 0.0267        | 19.49 (23%)     | 2   | 4   | 
| 7                | ap-northeast-2 | General purpose   | t2.large    | 0.1152        | 84.1           | 0.0346        | 25.26 (30%)     | 2   | 8   | 
| 8                | ap-northeast-2 | General purpose   | m5.large    | 0.118         | 86.14          | 0.0294        | 21.46 (25%)     | 2   | 8   | 
| 9                | ap-northeast-2 | General purpose   | m4.large    | 0.123         | 89.79          | 0.028         | 20.44 (23%)     | 2   | 8   | 
| 10               | ap-northeast-2 | Memory optimized  | r4.large    | 0.16          | 116.8          | 0.0293        | 21.39 (18%)     | 2   | 15  | 
| 11               | ap-northeast-2 | Storage optimized | i3.large    | 0.183         | 133.59         | 0.0549        | 40.08 (30%)     | 2   | 15  | 
| 12               | ap-northeast-2 | Compute optimized | c5.xlarge   | 0.192         | 140.16         | 0.0568        | 41.46 (30%)     | 4   | 8   | 
| 13               | ap-northeast-2 | Compute optimized | c4.xlarge   | 0.227         | 165.71         | 0.0533        | 38.91 (23%)     | 4   | 8   | 
| 14               | ap-northeast-2 | General purpose   | t2.xlarge   | 0.2304        | 168.19         | 0.0691        | 50.44 (30%)     | 4   | 16  | 
| 15               | ap-northeast-2 | General purpose   | m5.xlarge   | 0.236         | 172.28         | 0.0588        | 42.92 (25%)     | 4   | 16  | 
| 16               | ap-northeast-2 | General purpose   | m4.xlarge   | 0.246         | 179.58         | 0.056         | 40.88 (23%)     | 4   | 16  | 
| 17               | ap-northeast-2 | Memory optimized  | r4.xlarge   | 0.32          | 233.6          | 0.0587        | 42.85 (18%)     | 4   | 31  | 
| 18               | ap-northeast-2 | Storage optimized | i3.xlarge   | 0.366         | 267.18         | 0.1098        | 80.15 (30%)     | 4   | 31  | 
| 19               | ap-northeast-2 | Compute optimized | c5.2xlarge  | 0.384         | 280.32         | 0.112         | 81.76 (29%)     | 8   | 16  | 
| 20               | ap-northeast-2 | Compute optimized | c4.2xlarge  | 0.454         | 331.42         | 0.1067        | 77.89 (24%)     | 8   | 15  | 
| 21               | ap-northeast-2 | General purpose   | t2.2xlarge  | 0.4608        | 336.38         | 0.1382        | 100.89 (30%)    | 8   | 32  | 
| 22               | ap-northeast-2 | General purpose   | m5.2xlarge  | 0.472         | 344.56         | 0.1176        | 85.85 (25%)     | 8   | 32  | 
| 23               | ap-northeast-2 | General purpose   | m4.2xlarge  | 0.492         | 359.16         | 0.112         | 81.76 (23%)     | 8   | 32  | 
| 24               | ap-northeast-2 | Memory optimized  | r4.2xlarge  | 0.64          | 467.2          | 0.1174        | 85.70 (18%)     | 8   | 61  | 
| 25               | ap-northeast-2 | Storage optimized | i3.2xlarge  | 0.732         | 534.36         | 0.2196        | 160.31 (30%)    | 8   | 61  | 
| 26               | ap-northeast-2 | Compute optimized | c5.4xlarge  | 0.768         | 560.64         | 0.224         | 163.52 (29%)    | 16  | 32  | 
| 27               | ap-northeast-2 | Storage optimized | d2.xlarge   | 0.844         | 616.12         | 0.2532        | 184.84 (30%)    | 4   | 31  | 
| 28               | ap-northeast-2 | Compute optimized | c4.4xlarge  | 0.907         | 662.11         | 0.2134        | 155.78 (24%)    | 16  | 30  | 
| 29               | ap-northeast-2 | General purpose   | m5.4xlarge  | 0.944         | 689.12         | 0.2353        | 171.77 (25%)    | 16  | 64  | 
| 30               | ap-northeast-2 | General purpose   | m4.4xlarge  | 0.984         | 718.32         | 0.224         | 163.52 (23%)    | 16  | 64  | 
| 31               | ap-northeast-2 | Memory optimized  | r4.4xlarge  | 1.28          | 934.4          | 0.2347        | 171.33 (18%)    | 16  | 122 | 
| 32               | ap-northeast-2 | Storage optimized | i3.4xlarge  | 1.464         | 1068.72        | 0.4392        | 320.62 (30%)    | 16  | 122 | 
| 33               | ap-northeast-2 | GPU instance      | p2.xlarge   | 1.465         | 1069.45        | 0.4395        | 320.84 (30%)    | 4   | 61  | 
| 34               | ap-northeast-2 | Storage optimized | d2.2xlarge  | 1.688         | 1232.24        | 0.5064        | 369.67 (30%)    | 8   | 61  | 
| 35               | ap-northeast-2 | Compute optimized | c5.9xlarge  | 1.728         | 1261.44        | 0.5864        | 428.07 (34%)    | 36  | 72  | 
| 36               | ap-northeast-2 | Compute optimized | c4.8xlarge  | 1.815         | 1324.95        | 0.4268        | 311.56 (24%)    | 36  | 60  | 
| 37               | ap-northeast-2 | General purpose   | m4.10xlarge | 2.46          | 1795.8         | 0.5601        | 408.87 (23%)    | 40  | 160 | 
| 38               | ap-northeast-2 | Memory optimized  | r4.8xlarge  | 2.56          | 1868.8         | 0.4694        | 342.66 (18%)    | 32  | 244 | 
| 39               | ap-northeast-2 | General purpose   | m5.12xlarge | 2.832         | 2067.36        | 0.7058        | 515.23 (25%)    | 48  | 192 | 
| 40               | ap-northeast-2 | Storage optimized | i3.8xlarge  | 2.928         | 2137.44        | 2.928         | 2137.44 (100%)  | 32  | 244 | 
| 41               | ap-northeast-2 | Storage optimized | d2.4xlarge  | 3.376         | 2464.48        | 1.0128        | 739.34 (30%)    | 16  | 122 | 
| 42               | ap-northeast-2 | Compute optimized | c5.18xlarge | 3.456         | 2522.88        | 1.0082        | 735.99 (29%)    | 72  | 144 | 
| 43               | ap-northeast-2 | General purpose   | m4.16xlarge | 3.936         | 2873.28        | 0.8962        | 654.23 (23%)    | 64  | 256 | 
| 44               | ap-northeast-2 | GPU instance      | p3.2xlarge  | 4.981         | 3636.13        | 1.4943        | 1090.84 (30%)   | 8   | 61  | 
| 45               | ap-northeast-2 | Memory optimized  | r4.16xlarge | 5.12          | 3737.6         | 0.9389        | 685.40 (18%)    | 64  | 488 | 
| 46               | ap-northeast-2 | General purpose   | m5.24xlarge | 5.664         | 4134.72        | 1.4115        | 1030.39 (25%)   | 96  | 384 | 
| 47               | ap-northeast-2 | Storage optimized | i3.16xlarge | 5.856         | 4274.88        | 1.7568        | 1282.46 (30%)   | 64  | 488 | 
| 48               | ap-northeast-2 | Storage optimized | d2.8xlarge  | 6.752         | 4928.96        | 2.0256        | 1478.69 (30%)   | 36  | 244 | 
| 49               | ap-northeast-2 | Memory optimized  | x1.16xlarge | 9.671         | 7059.83        | 2.9013        | 2117.95 (30%)   | 64  | 976 | 
| 50               | ap-northeast-2 | GPU instance      | p2.8xlarge  | 11.72         | 8555.6         | 11.72         | 8555.60 (100%)  | 32  | 488 | 
| 51               | ap-northeast-2 | Memory optimized  | x1.32xlarge | 19.341        | 14118.93       | 19.341        | 14118.93 (100%) | 128 | 1   | 
| 52               | ap-northeast-2 | GPU instance      | p3.8xlarge  | 19.924        | 14544.52       | 19.924        | 14544.52 (100%) | 32  | 244 | 
| 53               | ap-northeast-2 | GPU instance      | p2.16xlarge | 23.44         | 17111.2        | 23.44         | 17111.20 (100%) | 64  | 768 | 
| 54               | ap-northeast-2 | GPU instance      | p3.16xlarge | 39.848        | 29089.04       | 39.848        | 29089.04 (100%) | 64  | 488 | 

