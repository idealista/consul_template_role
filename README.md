# Consul Template Ansible role
![Logo](https://raw.githubusercontent.com/idealista/consul_template_role/master/logo.gif)

[![Build Status](https://travis-ci.org/idealista/consul_template_role.png)](https://travis-ci.org/idealista/consul_template_role)
[![Ansible Galaxy](https://img.shields.io/badge/galaxy-idealista.consul_template_role-B62682.svg)](https://galaxy.ansible.com/idealista/consul_template_role)



This ansible role installs [Consul Template](https://github.com/hashicorp/consul-template) in a Debian environment. It has been tested for Debian buster and stretch.

This role has been generated using the [cookiecutter](https://github.com/cookiecutter/cookiecutter) tool, you can generate a similar role that fits your needs using the this [cookiecutter template](https://github.com/idealista/cookiecutter-ansible-role).

- [Getting Started](#getting-started)
	- [Prerequisities](#prerequisities)
	- [Installing](#installing)
- [Usage](#usage)
- [Testing](#testing)
- [Built With](#built-with)
- [Versioning](#versioning)
- [Authors](#authors)
- [License](#license)
- [Contributing](#contributing)

## Getting Started
These instructions will get you a copy of the role for your Ansible playbook. Once launched, it will install Consul Template in a Debian system.

### Prerequisities

Ansible 2.9.x.x version installed.

Molecule 3.x.x version installed.

For testing purposes, [Molecule](https://molecule.readthedocs.io/) with [Docker](https://www.docker.com/) as driver and  [Goss] (https://github.com/aelsabbahy/goss) as verifier.

### Installing

Create or add to your roles dependency file (e.g requirements.yml):

```
- src: idealista.consul_template_role
  version: 1.0.0
  name: consul_template_role
```

Install the role with ansible-galaxy command:

```
ansible-galaxy install -p roles -r requirements.yml -f
```

Use in a playbook:

```
---
- hosts: someserver
  roles:
    - role: consul_template_role
```

## Usage

Look to the [defaults](defaults/main.yml) properties file to see the possible configuration properties.

To use a custom template override the ```consul_template_template_src``` variable with the path of your template file. It is very likely that you need to do this because the default one only gets the list of nodes in consul.

To change the location where the template is rendered override the ```consul_template_render_path``` variable.

### Using the default configuration file

The default configuration allows you to do the things that you most likely need. When using it:

* You **must** define the ```consul_host``` variable in order to connect to consul.
* To use token authentication define the ```consul_token``` variable with the desired token.
* To use user and password authentication define the ```consul_user``` and ```consul_pass``` variables with the user and password.
* To use exec-mode define the ```consul_template_exec``` variable with the command to be executed.

You have more options in the configuration section of the [defaults](defaults/main.yml) file.

### Using a custom configuration file

If you want to use a custom configuration file override the ```consul_template_config_src``` variable with the path to you config file.

## Testing

### Install dependencies

```sh
$ pipenv sync
```

For more information read the [pipenv docs](ipenv-fork.readthedocs.io/en/latest/).

### Testing

```sh
$ pipenv run molecule test 
```

## Built With

![Ansible](https://img.shields.io/badge/ansible-2.9.9-green.svg)
![Molecule](https://img.shields.io/badge/molecule-3.0.4-green.svg)
![Goss](https://img.shields.io/badge/goss-0.3.11-green.svg)

## Versioning

For the versions available, see the [tags on this repository](https://github.com/idealista/consul_template_role/tags).

Additionaly you can see what change in each version in the [CHANGELOG.md](CHANGELOG.md) file.

## Authors

* **Idealista** - *Work with* - [idealista](https://github.com/idealista)

See also the list of [contributors](https://github.com/idealista/consul_template_role/contributors) who participated in this project.

## License

![Apache 2.0 License](https://img.shields.io/hexpm/l/plug.svg)

This project is licensed under the [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0) license - see the [LICENSE](LICENSE) file for details.

## Contributing

Please read [CONTRIBUTING.md](.github/CONTRIBUTING.md) for details on our code of conduct, and the process for submitting pull requests to us.
