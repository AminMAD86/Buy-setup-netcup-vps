# Buy & setup vps from netcup
Netcup is one of the best vps providers with high performance and cheap servers.

Link:
https://www.netcup.com/en/

If you wanna run both rpc and aztec node on your vps, I suggest "VPS 4000 ARM G11".

Click on order now, fill the details and confirm your order.
# Payment
They'll email you your ccp login credentials which you can manage the payments and pay for your server. It doesn't support crypto payments.
ccp website: 
https://www.customercontrolpanel.de/

*if you are from a restricted country like me and there's no payment option for you, you can get visa card from "paywithmoon" and add funds to it with crypto (Btc and usdt)
# manage vps
After paying for your server, they'll email you your vps ip and password and scp login credentials. 
In scp you can manage your vps. Link:
https://www.servercontrolpanel.de/SCP/
# client 
After getting your vps, you need a client to connect to your vps through SSH. Download and use moboxterm or termius.

search them in google
(personally I'm using moboxterm pro cracked version)
# connect to your vps
Connect to the vps via Mobaxterm

1- Click session and open SSH tab

2- Enter root@yourIPaddress in remote host

3- Click on OK and then a terminal opens which needs your password, Copy it & Paste it in the terminal by clicking Mouse Middle Scroll Wheel. (Password will be hidden in terminal)

you have successfully connected to your vps.
# config your vps
You should config your vps. Netcup uses Debian OS and German language for their servers. there's not much difference between debian and ubuntu so don't worry 

# change the language to English:
If you browse their website in english, your default language on both the control panels and your server will be english. but if your vps language was German, do the steps below:
```bash
sudo dpkg-reconfigure locales
```
go through the whole list and deselect the German language. 

Than select : en_US.UTF8

move up/down - using the arrows key
space key - select or deselect

tab key - to change the button ( move to OK button once done and press enter)
# install docker
```bash
sudo apt update -y && sudo apt upgrade -y

# Remove any existing Docker packages
for pkg in docker.io docker-doc docker-compose podman-docker containerd runc; do
  sudo apt-get remove -y $pkg
done

# Install required packages for Docker repo
sudo apt-get update
sudo apt-get install -y ca-certificates curl gnupg

# Create keyrings directory
sudo install -m 0755 -d /etc/apt/keyrings

# Add Docker GPG key
curl -fsSL https://download.docker.com/linux/debian/gpg | sudo gpg --dearmor -o /etc/apt/keyrings/docker.gpg
sudo chmod a+r /etc/apt/keyrings/docker.gpg

# Add Docker repository for Debian
echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.gpg] https://download.docker.com/linux/debian \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null

# Update package index
sudo apt update -y && sudo apt upgrade -y

# Install Docker packages
sudo apt-get install -y docker-ce docker-ce-cli containerd.io docker-buildx-plugin docker-compose-plugin

# Test Docker installation
sudo docker run hello-world

# Enable and restart Docker
sudo systemctl enable docker
sudo systemctl restart docker
```

# Install screen:
```bash
sudo apt update
sudo apt install screen -y
```

Done. Now you can run any node on your vps
