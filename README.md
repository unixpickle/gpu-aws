# gpu-aws

This will be a script to quickly create and manage GPU instances on AWS. It will be able to setup Go and [unixpickle/cuda](https://github.com/unixpickle/cuda) automatically. With this tool, it should be painless to train [anynet](https://github.com/unixpickle/anynet) models on AWS.

# Prerequisites

Most importantly, you must [setup the aws CLI](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-set-up.html).

You will want to use an AMI with CUDA support. To do this, checkout [NVIDIA CUDA Toolkit 7.5 on Amazon Linux](https://aws.amazon.com/marketplace/pp/B01LZMLK1K). If you choose the "Manual Launch" option, the AMI is free. Make sure you note the AMI ID for the region you intend to use.

In order to use `p2.xlarge` instances on AWS, you have to request a limit increase. To do this, go to the EC2 management console and then click on "Limits".

You may want to add `gpu-aws` to a directory in your `PATH` so that you get an actual `gpu-aws` command.

# Usage

First, you'll want to create a new session. A session manages a single EC2 instance. Decide on a session path (a directory which will be created by `gpu-aws`), the AWS instance type (e.g. t2.nano), and the AMI (e.g. [ami-4191b524](https://aws.amazon.com/amazon-linux-ami/)). Now you can create a session like so:

```
$ export SESSDIR=~/my_session
$ gpu-aws create $SESSDIR t2.nano ami-4191b524
Creating key pair...
Checking security group...
Security group already exists.
Creating t2.nano from AMI ami-4191b524...
Getting instance IP...
IP: 123.123.123.123
```

The new instance is now running. You will probably want to configure Go, git, and other important tools:

```
$ gpu-aws setup | gpu-aws ssh $SESSDIR ec2-user
```

You can SSH into the instance like so:

```
$ gpu-aws ssh $SESSDIR ec2-user
```

When you are done with the instance, you can terminate it like so:

```
$ gpu-aws destroy $SESSDIR
$ rm -r $SESSDIR
```

# TODO

 * Finish `setup` command
   * Setup unixpickle/cuda env vars
