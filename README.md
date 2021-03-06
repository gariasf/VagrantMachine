# VagrantMachine

A vagrant machine provisioned with **Ubuntu 14 Server LTS**, **Docker**, **.Net Core 2.2 SDK** and **Visual Studio**

### Prepare your computer to run vagrant (VirtualBox) machines

Vagrant runs VBox machines. If you use docker or any Hyper-V powered tools, you'll need to create a new Windows 10 boot with Hyper-V disabled.
You can use `bcdedit` to do so by following these steps:

- Open CMD with administrator privileges.
- Run `bcdedit /export bootmgr.bak` to create a backup of your bootloader configuration.
- Run `bcdedit /copy {current} /d "TagName"` to create a new bootloader entry with the specified tag (TagName is what will be shown in the selection menu). A response like `The entry was successfully copied to {guid}` should show up. Copy that guid.
- Run `bcdedit /set {guid} hypervisorlaunchtype off` to disable Hyper-V on the newly created bootloader entry. Remember to paste the guid you copied inside the brackets.
- Restart into your new windows boot entry.

## Building the machine

Clone this repo and enter the repo directory
```shell
$ git clone https://github.com/gariasf/VagrantMachine.git
$ cd VagrantMachine
```

If you're not into cloning repos, you can just create the VAGRANTFILE and bootsrtap.sh files yourself and then fill the contents based on the ones here online.

Run the vagrant up command
```
$ vagrant up
```

That should build and run the machine. The first time takes a while, so sit back and relax. Brew some tea if you prefer.

If the first run doesn't boot up and gets frozen at `Loading extension GLX`, close the machine (from VirtualBox works) and open it up agran. You don't need to run vagrant up again.

Default username/password is `vagrant/vagrant`


## Getting the machine from vagrant cloud
You can also use this machine by fetching it from the vagrant cloud like so:

```ruby
Vagrant.configure("2") do |config|
  config.vm.box = "gariasf/UbNETvDo"
  config.vm.box_version = "0.1.0"
end
```
