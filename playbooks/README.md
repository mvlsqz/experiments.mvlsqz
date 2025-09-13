# Experimental Playbook

## Environment setup
`adt` includes the `ansible-creator` tool that helps to bootstrap the testing playbook.

To do so, run the following command:

```bash
ansible-creator init playbook experiments.mvlsqz playbooks/experimental-playbook
```


## Included content/ Directory Structure

The directory structure follows best practices recommended by the Ansible
community, letting us with the following structure:

```
 playbooks/experimental-playbook/
 |── linux_playbook.yml
 |── README.md
```

# Molecule
So what is Molecule?
> Molecule leverages standard Ansible features including inventory, playbooks, and collections to provide flexible testing workflows. Test scenarios can target any system or service reachable from Ansible, from containers and virtual machines to cloud infrastructure, hyperscaler services, APIs, databases, and network devices. Molecule can also validate inventory configurations and dynamic inventory sources.
-- Molecule documentation

Then based on what the documentation says, we are going to setup our molecule
testing environment to target a set of containers that will mimic our real infrastructure.

## Bootstrapping our first scenario
The concept of a scenario is to have a set of resources that will validate our playbook in different contexts, by having in mind our actual infrastructure or environment constraints. The most simplest way from my perspective is that for testing purposes to bring up a set of Linux containers, those are easy to manage, cheap and fast.

Stop talking and show me the code!

```bash
molecule init scenario linux # name the scenario to something that makes sense to the playbook you are testing
```

This will create a `molecule/` directory with an skeleton structure for testing out the playbook

## The molecule.yml file


## Compatible with Ansible-lint

Tested with ansible-lint >=24.2.0 releases and the current development version
of ansible-core.
