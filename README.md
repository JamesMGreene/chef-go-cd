# [`gocd_agent` Chef Cookbook](https://github.com/JamesMGreene/chef-gocd-agent) [![GitHub Latest Release](https://badge.fury.io/gh/JamesMGreene%2Fchef-gocd-agent.png)](https://github.com/JamesMGreene/chef-gocd-agent) [![Build Status](https://secure.travis-ci.org/JamesMGreene/chef-gocd-agent.png?branch=master)](https://travis-ci.org/JamesMGreene/chef-gocd-agent) [![Chef Cookbook](http://img.shields.io/cookbook/v/gocd_agent.svg)](https://supermarket.chef.io/cookbooks/gocd_agent)

Install and configure a ThoughtWorks Go CD (GoCD) Agent/Client.


## Supported Platforms

### Verified

 - **RHEL:** Amazon Linux


### Unverified

 - **RHEL:** RedHat, CentOS, Scientific, Oracle, Fedora, etc.
 - **Debian:** Debian, Ubuntu, LinuxMint, etc.
 - **MacOS X:** MacOS X, MacOS X Server, etc.
 - **Windows:** Windows, MinGW32, MSWin, etc.
 - **Solaris:** Solaris, Solaris2, OpenSolaris, OmniOS, SmartOS, etc.



## Requirements

### Other Cookbooks
- `java` - GoCD Agents require that OpenJDK/Java 7 is installed.


### `package`s
- `unzip` - In some logic branches, the `unzip` utility method will be used to decompress an archive file.



## Attributes

### Primary

```chef
# The Basics
default[:gocd_agent][:name]    = 'go-agent'
default[:gocd_agent][:version] = '15.2.0'
default[:gocd_agent][:release] = '2248'

# Configure communication with the GoCD Server
default[:gocd_agent][:gocd_server][:host] = '127.0.0.1'
default[:gocd_agent][:gocd_server][:port] = 8153

# Auto-register new GoCD Agents with the GoCD Server?
default[:gocd_agent][:auto_register][:key]          = nil
default[:gocd_agent][:auto_register][:resources]    = []
default[:gocd_agent][:auto_register][:environments] = []
# Requires GoCD 15.2.0 or higher
default[:gocd_agent][:auto_register][:hostname]     = node[:hostname]
```


### Secondary

There are many other attributes specified for this cookbook.  To see them in full, review the code: [attributes/default.rb](https://github.com/JamesMGreene/chef-gocd-agent/blob/master/attributes/default.rb)



## Usage

Include the `gocd_agent` default recipe to install a GoCD Agent/Client on your system based on the default installation method:

```chef
include_recipe 'gocd_agent'
```

**Synonyms:** `gocd_agent::default`, `gocd_agent::install`


### Directed Install Methods

#### Package

Install the GoCD Agent from official packages [but _without_ using repos]:

```chef
# Not necessary to set because it's the default, when available on a platform
node[:gocd_agent][:install_method] = 'package'
include_recipe 'gocd_agent'

# OR:

include_recipe 'gocd_agent::install_from_package'
```


#### Binary

Install the GoCD Agent from official prebuilt binaries:

```chef
# Not necessary to set because it's the default, when available on a platform
node[:gocd_agent][:install_method] = 'binary'
include_recipe 'gocd_agent'

# OR:

include_recipe 'gocd_agent::install_from_binary'
```


#### Source

Install the GoCD Agent from the released source archive:

```chef
# Not necessary to set because it's the default, when nothing else is available on a platform
node[:gocd_agent][:install_method] = 'source'
include_recipe 'gocd_agent'

# OR:

include_recipe 'gocd_agent::install_from_source'
```



## Contributing

1. Fork the repository on GitHub
2. Create a named feature branch (like `add_component_x`)
3. Write your change
4. Write tests for your change (if applicable)
5. Run the tests, ensuring they all pass (if applicable)
6. Submit a Pull Request using GitHub


## License

Copyright (c) 2015, James M. Greene (MIT License)
