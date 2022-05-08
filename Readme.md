# DyalogAPL on WSL2 with Ubuntu 22.04 LTS
DyalogAPL needs Dotnet Core 3.1 at the moment and Dotnet core 3.1 needs Openssl 1.1
### Openssl 1.1
You can install Openssl 1.1 with the following commands:
```sh
echo "deb http://security.ubuntu.com/ubuntu impish-security main" | sudo tee /etc/apt/sources.list.d/impish-security.list
sudo apt-get update
sudo apt-get install libssl1.1
```
### Dotnet 3.1
You can install Dotnet 3.1 with the following commands:
```sh	
sudo wget https://packages.microsoft.com/config/ubuntu/20.04/packages-microsoft-prod.deb -O packages-microsoft-prod.deb
sudo dpkg -i packages-microsoft-prod.deb
sudo add-apt-repository universe
sudo apt-get update
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-3.1
```

## DyalogAPL
For Dyalog APL you just need to install the following packages:
```sh
sudo apt install libtinfo5
sudo dpkg --install  linux_64_18.2.45405_unicode.x86_64.deb
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