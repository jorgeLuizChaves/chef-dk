# Next Version (unreleased)

# ChefDK 3.3 Release Notes

## Chef 14.5.33

ChefDK now ships with Chef 14.5.33\. See <https://docs.chef.io/release_notes.html> for more information on what's new.

## New Functionality

* New option: `chef update --exclude-deps` for policyfiles will only update the cookbook(s) given on the command line.

## Updated Tooling

### ChefSpec

ChefSpec 7.3.2 greatly simplifies the syntax as well as allows testing of custom resources.
See the [README](https://github.com/chefspec/chefspec/blob/v7.3.2/README.md) and especially the section on
[testing custom resoures](https://github.com/chefspec/chefspec/blob/v7.3.2/README.md#testing-a-custom-resource) for
examples of the new syntax.

## Updated Components and Tools

* `chef-provisioning-aws`: 3.0.4 -> 3.0.6
* `chef-vault`: 3.3.0 -> 3.4.2
* `foodcritic`: 14.0.0 -> 14.1.0
* `inspec`: 2.2.70 -> 2.2.112
* `kitchen-inspec`: 0.23.1 -> 0.24.0
* `kitchen-vagrant`: 1.3.3 -> 1.3.4

## Deprecations

* `chef generate app` - Application repos were a pattern that didn't take off.
* `chef generate lwrp` - Use `chef generate resource`. Every supported release of Chef knows about custom resources. Custom resources are awesome. No one should be writing new LWRPs any more. LWRPS are not awesome.

# ChefDK 3.2 Release Notes

## Chef 14.4.56

ChefDK now ships with Chef 14.4.56\. See <https://docs.chef.io/release_notes.html> for more information on what's new.

## New Functionality

* New `chef describe-cookbook` command to display the cookbook checksum.
* Change policyfile generator to use 'policyfiles' directory instead of 'policies' directory

## New Tooling

### Chef Apply

[Chef Apply](https://github.com/chef/chef-apply) is the new gem which provides ad-hoc node management via the `chef-run` binary. It is included in the ChefDK only as a stepping stone towards managing gem resolution in the Chef Workstation repository. Please continue to download and install Chef Workstation if you wish to use the ad-hoc functionality. No guarantees for backwards compatability or functionality are made for the Chef Apply gem when used via the ChefDK.

### Kitchen AzureRM

ChefDK now includes a driver for [Azure Resource Manager](https://github.com/test-kitchen/kitchen-azurerm). This allows Microsoft Azure resources to be provisioned prior to testing. This driver uses the new Microsoft Azure Resource Management REST API via the azure-sdk-for-ruby.

## Updated Tooling

### Test Kitchen

Test Kitchen 1.23 now includes support for [lifecycle hooks](https://github.com/test-kitchen/test-kitchen/blob/master/RELEASE_NOTES.md#life-cycle-hooks).

## Updated Components and Tools

- `berkshelf`: 7.0.4 -> 7.0.6
- `chef-provisioning`: 2.7.1 -> 2.7.2
- `chef-provisioning-aws`: 3.0.2 -> 3.0.4
- `chef-sugar`: 4.0.0 -> 4.1.0
- `fauxhai`: 6.4.0 -> 6.6.0
- `inspec`: 2.1.72 ->2.2.70
- `kitchen-google`: 1.4.0 -> 1.5.0

## Security Updates

### OpenSSL

OpenSSL updated to 1.0.2p to resolve:
- Client DoS due to large DH parameter ([CVE-2018-0732](https://nvd.nist.gov/vuln/detail/CVE-2018-0732))
- Cache timing vulnerability in RSA Key Generation ([CVE-2018-0737](https://nvd.nist.gov/vuln/detail/CVE-2018-0737))

# ChefDK 3.1 Release Notes

## Chef 14.2.0

ChefDK now ships with Chef 14.2.0\. See <https://docs.chef.io/release_notes.html> for more information on what's new.

## Habitat packages available

ChefDK is now released as a habitat package under the identifier `chef/chef-dk`. All successful builds will be available in the `unstable` channel and all promoted builds will be available in the `stable` channel. This is similar to the `current` and `stable` downloads of ChefDK available on <https://downloads.chef.io/chefdk/stable>.

## Updated Homebrew cask tap

On macOS you can install ChefDK using `brew cask install chef/chef/chefdk`. This behavior is not new but the tap name changed.

## Updated Tooling

### Fauxhai

Fauxhai 6.4.0 brings support for 3 new platforms - CentOS 7.5, Debian 8.11, and FreeBSD 11.2. It also updates the dumps for Amazon Linux, Redhat, SLES, and Ubuntu to match Chef 14.2 output. Finally it deprecates FreeBSD 10.3.

### Foodcritic

Foodcritic 14.0.0 adds support for Chef 14.2 metadata, makes it the default, and removes old Chef 13 metadata. It also updated rules for clarity, removed an unecessary rule, and added a new rule saying when cookbooks have unecessary dependencies now that resources moved into core Chef. See the [changelog](https://github.com/Foodcritic/foodcritic/blob/master/CHANGELOG.md#1400-2018-06-28) for a full list of changes.

### knife-acl

[knife-acl](https://github.com/chef/knife-acl) is now included with ChefDK. This knife plugin allows admin users to modify Chef Server ACLs from their command line.

### knife-tidy

[knife-tidy](https://github.com/chef-customers/knife-tidy) is now included with ChefDK. This knife plugin generates reports about stale nodes and helps clean them up.

### Test Kitchen

Test Kitchen 1.11.0 adds a new `ssh_gateway_port` config and fixed a bug on Unix systems where scripts were not created as executable.

## Updated Components and Tools

- `fauxhai`: 6.3.0 -> 6.4.0
- `foodcritic`: 13.1.1 -> 14.0.0
- `kitchen-digitalocean`: 0.9.8 -> 0.10.0
- `knife-opc`: 0.3.2 -> 0.4.0
- `test-kitchen`: 1.21.2 ->1.22.0

## Security Updates

### OpenSSL

OpenSSL updated to 1.0.2p to resolve:
- Client DoS due to large DH parameter ([CVE-2018-0732](https://nvd.nist.gov/vuln/detail/CVE-2018-0732))
- Cache timing vulnerability in RSA Key Generation ([CVE-2018-0737](https://nvd.nist.gov/vuln/detail/CVE-2018-0737))

- `CVE-2018-1000201`: DLL loading issue which can be hijacked on Windows OS

# ChefDK 3.0 Release Notes

## Chef 14.1.1

ChefDK now ships with Chef 14.1.1\. See <https://docs.chef.io/release_notes.html> for more information on what's new.

## Updated Operating System support

ChefDK now ships packages for Ubuntu 18.04 and Debian 9. In accordance with Chef's platform End Of Life policy, ChefDK is no longer shipped on macOS 10.10.

## Enhanced cookbook archive handling

ChefDK now uses an embedded copy of libarchive to support Policyfile and Berkshelf. This improves overall performance and provides a well tested interface to many different types of archives. It also resolves the long standing "not an octal string" problem users face when depending on certain cookbooks in the supermarket.

## Policyfiles: updated `include_policy` support

Policyfiles now support git targets for included policies.

```
include_policy 'base_policy',
               git: 'https://github.com/happychef/chef-repo.git',
               branch: master,
               path: 'policies/base/Policyfile.lock.json'
```

## Policyfiles: `chef update` gains `--exclude-deps` flag

When using this, behavior is very strict: it updates only the cookbook(s)
mentioned on command line.

## Updated Tooling

### Test Kitchen

Test Kitchen has been updated from 1.20.0 to 1.21.2. This release allows you to use a kitchen.yml config file instead of .kitchen.yml so the kitchen config will no longer be hidden in your cookbook directories. It also introduces new config options for SSH proxy servers and allows you to specify multiple paths for data bags. See <https://github.com/test-kitchen/test-kitchen/blob/master/CHANGELOG.md> for the complete list of changes.

### InSpec

InSpec has been updated from 1.51.21 to 2.1.68. InSpec 2.0 brings compliance automation to the cloud, with new resource types specifically built for AWS and Azure clouds. Along with these changes are major speed improvements and quality of life updates. Please visit <https://www.inspec.io> for more information.

### ChefSpec

ChefSpec has been updated to 7.2.1 with Fauxhai 6.2.0. This release removes all platforms that were previously marked as deprecated in Fauxhai. If you saw Fauxhai deprecation warnings during your ChefSpec runs these will now be failures. This update also adds 9 new platforms and updates existing data for Chef 14. To see a complete list of platforms that can be mocked in ChefSpec see <https://github.com/chefspec/fauxhai/blob/master/PLATFORMS.md>.

### Foodcritic

Foodcritic has been updated to from 12.3.0 to 13.1.1. This updates Foodcritic for Chef 13 or later by removing Chef 12 metadata and removing several legacy rules that suggested writing resources in a Chef 12 manner. The update also adds 9 new rules for writing custom resources and updating cookbooks to Chef 13 and 14, resolves several long standing file detection bugs, and improves performance.

### Cookstyle

Cookstyle has been updated to 3.0, which updates the underlying RuboCop engine to 0.55 with a long list of bug fixes and improvements. This release of Cookstyle also enables 19 new rules available in RuboCop. See <https://github.com/chef/cookstyle/blob/master/CHANGELOG.md> for a complete list of newly enabled rules.

### Berkshelf

Berkshelf has been updated to 7.0.2.  Berkshelf 7 moves to using the same libraries as the Chef Client, ensuring consistent behaviour - for instance, ensuring that chefignore files work the same - and enabling a quicker turnaround on bug fixes.  The “Actor crashed” failures of celluloid will no longer be produced by Berkshelf.

### VMware vSphere support

The knife-vsphere plugin for managing VMware vSphere is now bundled with ChefDK.

## Cookbook generator creates a CHANGELOG.md

`chef cookbook generate [cookbook_name]` now creates a `CHANGELOG.md` file.

## Updated Components and Tools

- `chef-provisioning` 2.7.0 -> 2.7.1
- `knife-ec2` 0.17.0 -> 0.18.0
- `opscode-pushy-client` 2.3.0 -> 2.4.11

## Security Updates

### Ruby

Ruby has been updated to 2.5.1 to resolve the following vulnerabilities:

- `CVE-2017-17742`: HTTP response splitting in WEBrick
- `CVE-2018-6914`: Unintentional file and directory creation with directory traversal in tempfile and tmpdir
- `CVE-2018-8777`: DoS by large request in WEBrick
- `CVE-2018-8778`: Buffer under-read in String#unpack
- `CVE-2018-8779`: Unintentional socket creation by poisoned NUL byte in UNIXServer and UNIXSocket
- `CVE-2018-8780`: Unintentional directory traversal by poisoned NUL byte in Dir
- Multiple vulnerabilities in RubyGems

### OpenSSL

OpenSSL has been updated to 1.0.2o to resolve `CVE-2018-0739`.

# ChefDK 2.5 Release Notes

## Rename `smoke` tests to `integration` tests.

The cookbook, recipe, and app generators now name the test directory `integration` instead of `smoke`.

## Chef 13.8.5

ChefDK now ships with Chef 13.8.5. See <https://docs.chef.io/release_notes.html> for more information on what's new.

## Updated chef_version in chef generate cookbook

When running `chef generate cookbook` the generated cookbook will now specify a minimum chef release of 12.14 not 12.1.

## Security Updates

### Ruby

Ruby has been updated to 2.4.3 to resolve `CVE-2017-17405`

### OpenSSL

OpenSSL has been updated to 1.0.2n to resolve `CVE-2017-3738`, `CVE-2017-3737`, `CVE-2017-3736`, and `CVE-2017-3735`.

### LibXML2

LibXML2 has been updated to 2.9.7 to fix `CVE-2017-15412`

### minitar

minitar has been updated to 0.6.1 to resolve `CVE-2016-10173`

## Updated Components

- `chefspec` 7.1.2 -> 7.1.2
- `chef-api` 0.7.1 -> 0.8.0
- `chef-provisioning` 2.6.0 -> 2.7.0
- `chef-provisioning-aws` 3.0.0 -> 3.0.2
- `chef-sugar` 3.6.0 -> 4.0.0
- `foodcritic` 12.2.1 -> 12.3.0
- `inspec` 1.45.13 -> 1.51.21
- `kitchen-dokken` 2.6.5 -> 2.6.7
- `kitchen-ec2` 1.3.2 -> 2.2.1
- `kitchen-inspec` 0.20.0 -> 0.23.1
- `kitchen-vagrant` 1.2.1 -> 1.3.1
- `knife-ec2` 0.16.0 -> 0.17.0
- `knife-windows` 1.9.0 -> 1.9.1
- `test-kitchen` 1.19.2 -> 1.20.0
- `chef-provisioning-azure` has been removed as it used deprecated Azure APIs

# ChefDK 2.4 Release Notes

## Improved Performance Downloading Cookbooks from a Chef Server

Policyfile users who use a Chef Server as a cookbook source will experience faster cookbook downloads when running `chef install`. Chef Server's API requires each file in a cookbook to be downloaded separately; ChefDK will now download the files in parallel. Additionally, HTTP keepalives are enabled to reduce connection overhead.

## Cookbook Artifact Source for Policyfiles

Policyfile users may now source cookbooks from the Chef Server's cookbook artifact store. This is mainly intended to support the upcoming `include_policy` feature, but could be useful in some situations.

Given a cookbook that has been uploaded to the Chef Server via `chef push`, it can be used in another policy by adding code like the following to the ruby policyfile:

```
cookbook "runit",
  chef_server_artifact: "https://chef.example/organizations/myorg",
  identifier: "09d43fad354b3efcc5b5836fef5137131f60f974"
```

## Add include_policy directive
Policyfile maybe now use the `include_policy` directive as described in
[RFC097](https://github.com/chef/chef-rfc/blob/master/rfc097-policyfile-includes.md).
This directive's purpose is to allow the inclusion policyfile locks to the current
policyfile. In this iteration, we support sourcing lock files from a local path or a
chef server. Below is a simple example of how the `include_policy` directive can be used.

Given a policyfile `base.rb`:
```
name 'base'

default_source :supermarket

run_list 'motd'

cookbook 'motd', '~> 0.6.0'
```

Run:
```
>> chef install ./base.rb

Building policy base
Expanded run list: recipe[motd]
Caching Cookbooks...
Using      motd         0.6.4
Using      chef_handler 3.0.2

Lockfile written to /home/jaym/workspace/chef-dk/base.lock.json
Policy revision id: 1238e7a353ec07a4df6636cdffd8805220a00789bace96d6d70268a4b0064023
```

This will produce the `base.lock.json` that will be included in our next policy `users.rb`:
```
name 'users'

default_source :supermarket

run_list 'user'

cookbook 'user', '~> 0.7.0'

include_policy 'base', path: './base.lock.json'
```

Run:
```
>> chef install ./users.rb

Building policy users
Expanded run list: recipe[motd::default], recipe[user]
Caching Cookbooks...
Using      motd         0.6.4
Installing user         0.7.0
Using      chef_handler 3.0.2

Lockfile written to /home/jaym/workspace/chef-dk/users.lock.json
Policy revision id: 20fac68f987152f62a2761e1cfc7f1dc29b598303bfb2d84a115557e2a4a8f27
```

This will produce a `users.lock.json` that has the `base` policyfile lock merged in.

More information can be found in
[RFC097](https://github.com/chef/chef-rfc/blob/master/rfc097-policyfile-includes.md) and
the [docs](https://docs.chef.io/policyfile.htm://docs.chef.io/policyfile.html).

## New tools bundled

We are now shipping the following new tools as part of Chef-DK
  - kitchen-digitalocean
  - kitchen-google
  - knife-ec2
  - knife-google

## Chef Provisioning AWS uses AWS SDK v2

The Chef Provisioning AWS gem has been updated from the Amazon AWS SDK V1 to V2. This includes a huge number of under the hood improvements and bug fixes.

## Notable Updated Gems

- aws-sdk 2.10.45 -> 2.10.90
- chef 13.4.19 -> 13.6.4 ([Changelog](https://github.com/chef/chef/blob/master/RELEASE_NOTES.md))
- chefspec 7.1.0 -> 7.1.1 ([Changelog](https://github.com/chefspec/chefspec/blob/master/CHANGELOG.md)
- chef-provisioning 2.5.0 -> 2.6.0 ([Changelog](https://github.com/chef/chef-provisioning/blob/master/CHANGELOG.md))
- chef-provisioning-aws 2.2.2 -> 3.0.0 ([Changelog](https://github.com/chef/chef-provisioning-aws/blob/master/CHANGELOG.md))
- chef-provisioning-fog 0.21.0 -> 0.26.0 ([Changelog](https://github.com/chef/chef-provisioning-fog/blob/master/CHANGELOG.md))
- chef-sugar 3.5.0 -> 3.6.0 ([Changelog](https://github.com/sethvargo/chef-sugar/blob/master/CHANGELOG.md))
- fauxhai 5.3.0 -> 5.5.0 ([Changelog](https://github.com/chefspec/fauxhai/blob/master/CHANGELOG.md))
- foodcritic 11.4.0 -> 12.2.1 ([Changelog](https://github.com/Foodcritic/foodcritic/blob/master/CHANGELOG.md))
- inspec 1.36.1 -> 1.44.13 ([Changelog](https://github.com/chef/inspec/blob/master/CHANGELOG.md))
- kitchen-digitalocean new @ 0.9.8
- kitchen-google new @ 1.4.0
- kitchen-inspec 0.19.0 -> 0.20.0 ([Changelog](https://github.com/chef/kitchen-inspec/blob/master/CHANGELOG.md))
- knife-ec2 new @ 0.16.0
- knife-google new @ 3.2.0
- knife-spork 1.6.3 -> 1.7.1 ([Changelog](https://github.com/jonlives/knife-spork/blob/master/CHANGELOG.md))
- mixlib-install 2.1.12 -> 3.8.0 ([Changelog](https://github.com/chef/mixlib-install/blob/master/CHANGELOG.md))
- rspec 3.6.0 -> 3.7.0 ([Changelog](https://github.com/rspec/rspec-core/blob/master/Changelog.md))
- serverspec 2.40.0 -> 2.41.3
- test-kitchen 1.17.0 -> 1.19.2 ([Changelog](https://github.com/test-kitchen/test-kitchen/blob/master/CHANGELOG.md))
- train 0.26.2 -> 0.29.2 ([Changelog](https://github.com/chef/train/blob/master/CHANGELOG.md))
- winrm-fs 1.0.1 -> winrm-fs 1.1.1 ([Changelog](https://github.com/WinRb/winrm-fs/blob/master/changelog.md))


# ChefDK 2.3 Release Notes

ChefDK 2.3 includes Ruby 2.4.2 to fix the following CVEs:
  * CVE-2017-0898
  * CVE-2017-10784
  * CVE-2017-14033
  * CVE-2017-14064

The 2.2.1 release includes RubyGems 2.6.13 to fix the following CVEs:
  * CVE-2017-0899
  * CVE-2017-0900
  * CVE-2017-0901
  * CVE-2017-0902

ChefDK 2.3 includes:
  * Chef 13.4.19
  * InSpec 1.36.1
  * Berkshelf 6.3.1
  * Chef Vault 3.3.0
  * Foodcritic 11.4.0
  * Test Kitchen 1.17.0
  * Stove 6.0

## Stove is now included

We are now shipping stove in ChefDK, to aid users in uploading their
cookbooks to supermarkets.

## The cookbook generator now adds a LICENSE file

The cookbook generator now adds a LICENSE file when creating a new
cookbook.


## Boilerplate tests are generated for the CentOS platform
When `chef generate cookbook` is ran, boilerplate unit tests for the CentOS 7 platform are now generated as well.
