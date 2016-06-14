[![Code Climate](https://codeclimate.com/github/theforeman/foreman_azure/badges/gpa.svg)](https://codeclimate.com/github/theforeman/foreman_azure)
[![Gem Version](https://badge.fury.io/rb/foreman_azure.svg)](https://badge.fury.io/rb/foreman_azure)
[![GPL License](https://img.shields.io/github/license/theforeman/foreman_azure.svg)](https://github.com/theforeman/foreman_azure/blob/master/LICENSE)

# Foreman Azure

[Microsoft Azure](http://azure.com/) compute resource for [Foreman](http://theforeman.org/)

* Website: [theforeman.org](http://theforeman.org)
* ServerFault tag: [Foreman](http://serverfault.com/questions/tagged/foreman)
* Issues: [foreman Redmine](http://projects.theforeman.org/projects/foreman/issues)
* Wiki: [Foreman wiki](http://projects.theforeman.org/projects/foreman/wiki/About)
* Community and support: [#theforeman](https://kiwiirc.com/client/irc.freenode.net/?#theforeman) for general support, [#theforeman-dev](https://kiwiirc.com/client/irc.freenode.net/?#theforeman-dev) for development chat in [Freenode](irc.freenode.net)
* Mailing lists:
    * [foreman-users](https://groups.google.com/forum/?fromgroups#!forum/foreman-users)
    * [foreman-dev](https://groups.google.com/forum/?fromgroups#!forum/foreman-dev)


## Installation

See [the Foreman manual](https://theforeman.org/plugins/#2.2Packageinstallation)
for how to install Foreman plugins

## Configuration

When you create the compute resource, you need to provide your subscription ID, a path to the .pem certificate, and a URL to your Azure API

### Certificate creation

The certificate used must be generated by the user. OpenSSL can be used to create the management certificates. Two certificates are needed: a .cer file, which is uploaded to Azure, and a .pem file, which is stored locally.

To create the .pem file, execute the following command:

    openssl req -x509 -nodes -days 365 -newkey rsa:1024 -keyout /etc/foreman/azure.pem -out /etc/foreman/azure.pem

To create the .cer file, execute the following command:

    openssl x509 -inform pem -in /etc/foreman/azure.pem -outform der -out /etc/foreman/azure.cer

After creating these files, the .cer file will need to be uploaded to Azure via the "Upload a Management Certificate" action of the "Management Certificates" tab within the "Settings" section of the management portal.

## Pending

* foreman-installer support
* improve documentation

## Copyright

Copyright (c) 2016 Daniel Lobato Garcia

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program.  If not, see <http://www.gnu.org/licenses/>.

