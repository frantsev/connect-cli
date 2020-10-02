# Connect Command Line Interface

![pyversions](https://img.shields.io/pypi/pyversions/connect-cli.svg) [![PyPi Status](https://img.shields.io/pypi/v/connect-cli.svg)](https://pypi.org/project/connect-cli/) [![Build Status](https://travis-ci.org/cloudblue/connect-cli.svg?branch=master)](https://travis-ci.org/cloudblue/connect-cli) [![codecov](https://codecov.io/gh/cloudblue/connect-cli/branch/master/graph/badge.svg)](https://codecov.io/gh/cloudblue/connect-cli)


## Introduction

CloudBlue Connect is a supply automation platform that manages your products and services, contracts, 
ordering and fulfillment, usage and subscriptions. 

It supports any product, from physical goods to cloud products, as well as any channel, including your 
direct and indirect sales channels and internal procurement. 

With its flexible APIs, it can connect to any commerce platform.

Vendors can leverage CloudBlue Connect to:

* Reduce the total cost of ownership for homegrown technology supporting their indirect channel
* Standardize integrations with partners
* Increase efficiencies and minimize redundancies by bridging their direct and indirect sales channels

Service providers can use CloudBlue Connect to:

* Define, manage and distribute any type of product (omni-product) through any channel (omni-channel)
* Transform perpetual licensed products into a subscription model
* Onboard new products into their portfolio quickly to build and deliver unique solutions to end customers

`connect-cli` allow users to export/synchronize the items of a product to/from an Excel workbook.


## Install

### Using a virtualenv

To use `connect-cli` you need any *nix system with python 3.6 or later installed.

The preferred way to install `connect-cli` is using a [virtualenv](https://virtualenv.pypa.io/en/latest/):

```
    $ virtualenv psync
    $ source pysync/bin/activate
    $ pip install connect-cli
```    

### Binary distributions

A single executable binary distribution is available for windows, linux and mac osx (amd64).
You can it from the [Github Releases](https://github.com/cloudblue/connect-cli/releases) page.

To install under linux:

```
    $ curl -O -J https://github.com/cloudblue/connect-cli/releases/download/21.0/connect-cli_21.0_linux_amd64.tar.gz
    $ tar xvfz connect-cli_21.0_linux_amd64.tar.gz
    $ sudo cp dist/ccli /usr/local/bin/ccli
```

To install under Mac OSX:

```
    $ curl -O -J https://github.com/cloudblue/connect-cli/releases/download/21.0/connect-cli_21.0_osx_amd64.tar.gz
    $ tar xvfz connect-cli_21.0_osx_amd64.tar.gz
    $ sudo cp dist/ccli /usr/local/bin/ccli
```

> If your user is not a sudoer, you can copy the `ccli` executable from the dist directory to a directory of your choice
> that is listed in the `PATH` variable.


To install under Windows

Download the windows single executable zipfile from [Github Releases](https://github.com/cloudblue/connect-cli/releases/download/21.0/connect-cli_21.0_windows_amd64.tar.gz), extract it and place it in a folder that is included in your `path` system variable.


## Usage

### Add a new account

First of all you need to add an account the `connect-cli` with the CloudBlue Connect API *key*.

```
    $ ccli account add "ApiKey XXXXX:YYYYY"
```

### List configured accounts

To get a list of all configured account run:

```
    $ ccli account list
```


### Set the current active account

To set the current active account run:

```
    $ ccli account activate VA-000-000
```

### Remove an account

To remove an account run:

```
    $ ccli account remove VA-000-000
```

### List available products

To get a list of available products run:

```
    $ ccli product list
```

This command will output a list of all products (id and name) available within the current active account.
You can also filter the results by adding the ``--query`` flag followed by a RQL query.
For more information about RQL see the [Resource Query Language](https://connect.cloudblue.com/community/api/rql/)
article in the Connect community documentation portal.


### Export a product to Excel

To export a product to Excel run:

```
    $ ccli product export PRD-000-000-000
```

This command will generate a excel file named PRD-000-000-000.xlsx in the current working directory.


### Synchronize a product from Excel

To synchronize a product from Excel run:

```
    $ ccli product sync my_products.xlsx
```


### Getting help

To get help about the `connect-cli` commands type:

```
    $ ccli --help
```

## License

`connect-cli` is released under the [Apache License Version 2.0](https://www.apache.org/licenses/LICENSE-2.0).
