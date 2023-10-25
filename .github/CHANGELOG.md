# Changelog


# v0.1.9
_Released Oct 22, 2021_
## Modules affected 
* `log.sh`

## Description 
Added convenience function for echo-ing to `stderr`.
<br>

# v0.1.8
_Released Oct 8, 2021_
## Modules affected 
* `aws.sh`

## Description 
Introduce support for AWS Instance Metadata Service (IMDS) Version 2. These changes are fully backward compatible, and `bash-commons` continues to default to Version 1 of the Instance Metadata Service. 

You can override the version of IMDS that bash-commons contacts by setting the following environment variable: 

`GRUNTWORK_BASH_COMMONS_IMDS_VERSION="2"` 

`bash-commons` will continue to default to IMDSv1 until we have migrated all our dependent modules to use version 2. Once this migration is complete, we will issue another release that updates bash-commons to use IMDSv2 by default. 

For more information on the differences between Instance Metadata Service Versions 1 and 2 see [here](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/configuring-instance-metadata-service.html).

<br>

# v0.1.7
_Released Jun 11, 2021_
### Modules affected

* `assert.sh`
* `string.sh`


### Description

* Introduce `assert_user_has_sudo_perms` which checks if user has permissions to run `sudo`.
* Introduce `string_substr` which can extract a substring by index.

### Related links

* https://github.com/gruntwork-io/bash-commons/pull/37
<br>

# v0.1.6
_Released Jun 11, 2021_
### Modules affected

* `os.sh`

### Description

* Fix bug introduced with using `sudo` for the `os_create_user` and `os_change_dir_owner` functions.

### Related links

* https://github.com/gruntwork-io/bash-commons/pull/36
<br>

# v0.1.5
_Released Jun 10, 2021_
### Modules affected

* `os.sh`

### Description

* `os_create_user` and `os_change_dir_owner` now have the ability to run respective commands using `sudo`.

### Related links

* https://github.com/gruntwork-io/bash-commons/pull/35
<br>

# v0.1.4
_Released Apr 8, 2021_
### Modules affected

* `aws-wrapper.sh`

### Description

* Added a new `aws_wrapper_get_asg_rally_point` function that can calculate a "rally point" instance in an Auto Scaling Group (ASG) and return its hostname. This is a deterministic way for the instances in an ASG to all pick the same single instance to perform some action: e.g., this instance could become the leader in a cluster or run some initialization script that should only be run once for the entire ASG. Under the hood, this method picks the instance in the ASG with the earliest launch time; in the case of ties, the instance with the earliest instance ID (lexicographically) is returned. 

### Special thanks

* Thank you to @yardbirdsax for the contribution!

### Related links

* https://github.com/gruntwork-io/bash-commons/pull/33
<br>

# v0.1.3
_Released Sep 9, 2020_
### Modules affected

* `dynamic-ubuntu-wait.sh` [**NEW**]

### Description

Introduce a new helper script that can be used to wait for apt locks to be released. This is useful in infrastructure setup scripts (e.g. `packer`) where the nodes may start updating the packages as it is booting, preventing you from interacting with `apt`.

### Related links

* https://github.com/gruntwork-io/bash-commons/pull/4
<br>

# v0.1.2
_Released Mar 20, 2019_
### Modules affected

* `array.sh`
* `assert.sh`

### Description

* Fix syntax in the docs for the `array_split` function.
* Fix minor bug in the loop  indices of the `assert_exactly_one_of` function. 

### Related links

* https://github.com/gruntwork-io/bash-commons/pull/15
<br>

# v0.1.1
_Released Mar 5, 2019_
### Modules affected

- `array.sh`
- `assert.sh`
- `aws.sh`
- `file.sh`
- `os.sh`

### Description

- Extracted lots of great helper functions from `package-kafka` and `package-zookeeper` and moved them to `bash-commons`. These include `array_split`, `array_prepend`, `assert_exactly_one_of`, `file_replace_text_in_files`, `os_user_exists`, `os_create_user`, `os_change_dir_owner`, and a number of AWS EC2 and ENI functions. Check out the PR link below for the full list.

### Related links

- https://github.com/gruntwork-io/bash-commons/pull/14
<br>

# v0.1.0
_Released Nov 28, 2018_
### Modules affected

All!

### Description

* Add `bootstrap.sh` script that sets a number of good defaults, such as `pipefail`, `errtrace`, and `functrace`. We *strongly* recommend `source`ing this script at the very top of all of your scripts (i.e., before importing any of the other bash-commons scripts)!
* Use `#!/usr/bin/env bash` in all scripts instead of `#!/bin/bash`.
* Make scripts `shellcheck` compatible, fixing minor bugs along the way.

### Related links

* https://github.com/gruntwork-io/bash-commons/pull/11
<br>

# v0.0.7
_Released Oct 26, 2018_
#10 adds the `file_fill_template` function to replace a specific template string in a file with a value
<br>

# v0.0.6
_Released Sep 3, 2018_
#7 ensures `aws_get_instances_with_tag` returns only `pending` and `running` instances
<br>

# v0.0.5
_Released Aug 31, 2018_
#6 adds a new functions `aws_get_instances_with_tag` to `aws.sh` and `aws_wrapper_get_ips_with_tag` to `aws-wrapper.sh`
<br>

# v0.0.4
_Released Jun 22, 2018_
https://github.com/gruntwork-io/bash-commons/pull/5: Add an `os_is_redhat` method to `os.sh`.
<br>

# v0.0.3
_Released May 2, 2018_
#3 Fixed a minor issue in `os.sh` function `os_is_amazon_linux` where Amazon linux v1 and v2 had slightly different image names and we were not properly identifying Amazon linux in one of the cases.
<br>

# v0.0.2
_Released Apr 12, 2018_
https://github.com/gruntwork-io/bash-commons/pull/2: Fix two issues in `aws-wrapper.sh`: a broken `source` statement and a missing `assert_not_empty_or_null` in the `aws_wrapper_wait_for_instances_in_asg` method. Added tests for `aws.sh` and `aws-wrapper.sh` to try to prevent these sorts of bugs in the future.
<br>

# v0.0.1
_Released Apr 10, 2018_
https://github.com/gruntwork-io/bash-commons/pull/1: First release!
<br>

