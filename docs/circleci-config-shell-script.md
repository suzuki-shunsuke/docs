# Write shell scripts in files instead of in .circleci/config.yml

## Why?

* Minimize .circleci/config.yml
  * easy to read
* The editor can treat the code as shell script (format, lint, syntax highlight, code completion, etc)
* We will be able to lint shell scripts by some tools such as shfmt and shellckeck in the future
* We can compare two similar shell scripts with diff
* We can set the code owner of shell scripts
