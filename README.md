Vagrant Autopilot Version Upgrades for Consul using Build Tag
===========================

## Background

Consul has a feature called ["Autopilot"](https://learn.hashicorp.com/consul/day-2-operations/advanced-operations/autopilot):

On Consul Enterprise, Autopilot also has Upgrade Migrations

This repo is to demonstrate that feature, using `UpgradeVersionTag`

## Prerequisites

Make sure you have the enterprise binaries for Vault and Consul. The filenames
should look similar to this:

    consul-enterprise_1.4.3+ent_linux_amd64.zip

## Setup

 1. Clone this project from Github.
 2. Place the Consul binaries into the project folder.
 3. Install the `vagrant-hosts` plugin: `vagrant plugin install vagrant-hosts`
 4. Run `vagrant up /consul[0-5]/`
 5. Wait until all 5 servers are up
 7. Run `vagrant up /consulnew[0-5]` in a new terminal
 8. Wait until all 5 new servers are up
 9. `vagrant ssh consulnew0`
 10. `watch consul members`
 11. `vagrant destroy -f /consul[0-5]/`
 12. Watch how nodes will switch from failed to left, as Autopilot clears them out

## Screencast

![demo](https://user-images.githubusercontent.com/1064715/55078525-44216f80-5092-11e9-8c13-1b000875585d.gif)

## Documentation

https://learn.hashicorp.com/consul/day-2-operations/advanced-operations/autopilot#migrations-without-a-consul-version-change
