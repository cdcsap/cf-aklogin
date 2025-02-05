# CF Login tool [![Build Status](https://travis-ci.org/armakuni/cf-aklogin.svg?branch=master)](https://travis-ci.org/armakuni/cf-aklogin) [![Go Report Card](https://goreportcard.com/badge/github.com/armakuni/cf-aklogin)](https://goreportcard.com/report/github.com/armakuni/cf-aklogin) [![codecov](https://codecov.io/gh/armakuni/cf-aklogin/branch/master/graph/badge.svg)](https://codecov.io/gh/armakuni/cf-aklogin)

A tool that will allow switching between CF environments with a single command. 


### Install

	$ cf install-plugin -r CF-Community "cf-aklogin"

[Download the latest plugin](https://github.com/armakuni/cf-aklogin/releases) and run:
     
    $ cf install-plugin ~/Downloads/cf-aklogin.darwin
    
_Note: If you get `persmission denied`, run `chmod +x ~/Downloads/cf-aklogin.darwin`._

### Usage

#### Login

Create `~/.cflogin.yml`:
    
    include: //optional
    - ~/bar.yml
    foo:
      target: api.run.pivotal.io
      username: <username>
      password: <password>
      org: <org>
      space: <space>

_Note: leave password/org/space blank for `os.Stdin` input._

And then run:
    
    $ cf aklogin foo 

Or with your own `foo.yml`:

    include: //optional
    - ~/bar.yml
    foo:
      target: api.run.pivotal.io
      username: <username>
      password: <password> // optional
      org: <org> // optional
      space: <space> // optional

    $ cf aklogin -f foo.yml bar

#### List

    $ cf aklogin -h
    NAME:
       aklogin - CF login via profiles
    
    USAGE:
       cf aklogin [options] <profile>
    
    OPTIONS:
       --filename       YML config file path
       --list           List available profiles
       --version        Print version

    $ cf aklogin --list
    Available profiles:
    0. ak
    1. bar    
    2. foo
    Select profile: _
        
### Build and install
        
    $ make && make install
       
### Tests

    $ make test
	
### Release

    $ GITHUB_TOKEN=<your-token-here> make release
