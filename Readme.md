# DyalogAPL on WSL2 with Ubuntu 22.04 LTS
### Dotnet 6
You can install Dotnet 6.0 with the following command:
```bash	
sudo apt-get install dotnet6
```

## DyalogAPL
For Dyalog APL you just need to install the following packages:
```sh
sudo apt install libtinfo5
sudo dpkg --install  linux_64_18.2.45405_unicode.x86_64.deb
```
## Using .Net 6 with DyalogAPL 18.2
You can use .Net 6.0 with Dyalog according to John Daintre's instructions:
 
```
We will be supporting .NET 6.0 "out of the box" with the next version of Dyalog, 19.0 (I cannot say yet when that will be available).

Until then it should be possible to move to .NET 6.0 by making minor changes to some of Dyalog's configuration files. We cannot formally support this route, but I don't think there will be any problems.

In the dyalog installation you will see files called:

Dyalog.Net.Bridge.deps.json
Dyalog.Net.Bridge.runtimeconfig.json

Each of these files contains version strings which will include the fragment "3.1". Change those "3.1"s to "6.0"s and you should be good to go.

The following are the changes I made:

Dyalog.Net.Bridge.deps.json: "name": ".NETCoreApp,Version=v6.0",
Dyalog.Net.Bridge.deps.json: ".NETCoreApp,Version=v6.0": {
Dyalog.Net.Bridge.runtimeconfig.json: "tfm": "netcoreapp6.0",
Dyalog.Net.Bridge.runtimeconfig.json: "version": "6.0.0"


Best Regards
John Daintree
```

## Ride for Windows
You can download the latest version of Ride for Windows from [here](https://github.com/Dyalog/ride/releases).
## Starting RIDE on Windows by using DyalogAPL from WSL2 

Edit `/etc/ssh/sshd_config` on WSL2 with Ubuntu 22.04 LTS:<br>
Change `PasswordAuthentication no` to `PasswordAuthentication yes` <br>and restart `wsl2` by running `wsl --shutdown`

Then you can start RIDE on Windows with commands:
```
Type: `Start` and `SSH`
Host: `localhost`
User: `username`
Password: `password`
Interpreter: `Other` `/opt/mdyalog/18.2/64/unicode/mapl`
Environmental variables:
DYALOG_NETCORE=1
```

If you want to start `ride` manually, you can run following commands in Dyalog session:
```apl
3502⌶0             ⍝ Stop RIDE
3502⌶'SERVE::4502' ⍝ Update init string
3502⌶1             ⍝ Start RIDE
```
## Dyalog Keyboard on Windows
[Autohotkey](https://www.autohotkey.com/) is working nicely on Windows. You can use `dyalog.ahk` from the following repository: [autohotkey-dyalog](https://github.com/kimmolinna/autohotkey-dyalog)