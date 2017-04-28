# gpu-aws

This will be a script to quickly create and manage GPU instances on AWS. It will be able to setup Go and [unixpickle/cuda](https://github.com/unixpickle/cuda) automatically. With this tool, it should be painless to train [anynet](https://github.com/unixpickle/anynet) models on AWS.

# TODO

 * Add `setup` command
   * Download & install latest Go
   * Setup GOPATH
   * Setup unixpickle/cuda env vars
 * Add `push` and `pull` wrappers around scp
