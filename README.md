# gpu-aws

This will be a script to quickly create and manage GPU instances on AWS. It will be able to setup Go and [unixpickle/cuda](https://github.com/unixpickle/cuda) automatically. With this tool, it should be painless to train [anynet](https://github.com/unixpickle/anynet) models on AWS.

# Setup

In order to use this tool, you must [setup the aws CLI](http://docs.aws.amazon.com/cli/latest/userguide/cli-chap-getting-set-up.html). Doing so is fairly easy if you follow the instructions.

You will want to use an AMI with CUDA support. To do this, checkout [NVIDIA CUDA Toolkit 7.5 on Amazon Linux](https://aws.amazon.com/marketplace/pp/B01LZMLK1K). If you choose the "Manual Launch" option, the AMI is free. Make sure you note the AMI ID for the region you intend to use.

# TODO

 * Add `setup` command
   * Download & install latest Go
   * Setup GOPATH
   * Setup unixpickle/cuda env vars
