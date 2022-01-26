![Test status](https://github.com/johnae/sambal/actions/workflows/ci.yaml/badge.svg)

# Sambal

Sambal is a ruby samba client

Quite a bit of code was borrowed from https://github.com/reivilo/rsmbclient - Thanks!

## Installation

Add this line to your application's Gemfile:

    gem 'sambal'

And then execute:

    $ bundle

Or install it yourself as:

    $ gem install sambal

## Requirements

A working installation of samba, specifically the "smbclient" command line utility. See http://www.samba.org for more information.
On a mac this can be installed through homebrew https://github.com/mxcl/homebrew, like this:

    brew install samba

On Linux (Ubuntu) it's as easy as:

    apt-get install smbclient

It should be available in a similar way on all major Linux distributions.

If you happen to be running [NixOS](https://nixos.org/) or at least the [Nix package manager](https://nixos.org/nix/download.html) you could just
use the `default.nix` file in this repo. That should also set you up for running the tests (which require samba).

## Usage

    client = Sambal::Client.new(domain: 'WORKGROUP', host: '127.0.0.1', share: '', user: 'guest', password: '--no-pass', port: 445)
    client.ls # returns hash of files
    client.put("local_file.txt","remote_file.txt") # uploads file to server
    client.exists?("remote_file.txt") # checks if file is on server
    client.put_content("My content here", "remote_file") # uploads content to a file on server
    client.get("remote_file.txt", "local_file.txt") # downloads file from server
    client.del("remote_file.txt") # deletes files from server
    client.exists?("some_directory") # checks if directory is on server
    client.cd("some_directory") # changes directory on server
    client.close # closes connection

## Contributing

1. Fork it
2. Create your feature branch (`git checkout -b my-new-feature`)
3. Commit your changes (`git commit -am 'Added some feature'`)
4. Push to the branch (`git push origin my-new-feature`)
5. Create new Pull Request
