#!/bin/bash
 
 
##### START SYSTEM CLEANUP (Remove unnecessary apps/bloatware)
echo "Performimg system cleanup right now..."
sudo apt-get remove --purge libereoffice* orage* mirage* cups* hexchat* thunderbird* mpv* -y
sudo apt-get autoremove
echo "System cleanup succesfully performed!"
 
 
 
##### UPDATING RESPOSITORY & UPGRADING OS
echo "Updating respository and perfoming OS upgrade right now..."
sudo apt-get update && sudo apt-get upgrade -y
echo "Repository Update and OS Upgrade succesfully done!"
 
 
##### INSTALL DEPENDECIES FOR GO
echo "Installing GO dependencies right now..."
sudo apt-get install -y curl git mercurial make binutils gcc bzr bison libgmp3-dev screen build-essential
echo "GO ependencies succesfully installed!"
 
 
##### INSTALL GO LIBRARY
echo "Installing GO right now..."
###### Downloading GO source from Google servers using CURL
sudo curl -L https://dl.google.com/go/go1.9.2.linux-arm64.tar.gz -o go1.9.2.linux-arm64.tar.gz
###### Unzip the compressed GO source files
sudo tar -xvf go1.9.2.linux-arm64.tar.gz
###### Remove the downloaded compressed file (not needed anylonger!)
sudo rm go1.9.2.linux-arm64.tar.gz
###### Move GO folder to it's destination directory
sudo mv go /usr/local
###### Configure go enviroment variable
echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.profile
###### Reload the paths
sleep 5
. ~/.profile
###### Create GO directories
mkdir -p $HOME/go
mkdir -p $HOME/go/bin
mkdir -p $HOME/go/src
mkdir -p $HOME/go/pkg
###### Move GO folder
sudo mv go /usr/local/go
###### Create GO links
sudo ln -s /usr/local/go/bin/go /usr/local/bin/go
sudo ln -s /usr/local/go/bin/godoc /usr/local/bin/godoc
sudo ln -s /usr/local/go/bin/gofmt /usr/local/bin/gofmt
###### Return to root folder
cd ~
###### Configure $GOPATH variables
echo 'export GOROOT=/usr/local/go' >> ~/.bashrc
echo 'export GOPATH=$HOME/go' >> ~/.bashrc
echo 'export GOBIN=$GOPATH/bin' >> ~/.bashrc
echo 'export PATH=$PATH:$GOBIN' >> ~/.bashrc
###### Reload GO paths
sleep 5
. ~/.bashrc
echo "GO succesfully installed!"
 
 
##### INSTALL SKYCOIN
echo "Installing Skycoin right now..."
###### Obtain Skycoin source files from Github using GO
go get github.com/skycoin/skycoin/...
sleep 10
echo "Skycoin succesfully installed!"
cd $GOPATH/src/github.com/skycoin/skycoin

###### Launching Skycoin in the background
echo "Launching Skycoin Now"
make run > /dev/null 2>&1 &
sleep 60
echo "Skycoin is now running the wallet is synchronizing in the background"
sleep 5
 
#####################################################################   !!!!! SUPPORT FOR PUTTY GOES HERE !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! ########
 
 
##### INSTALL SKYWIRE
echo "Installing Skywire right now..."
###### Change the path for download
cd $GOPATH/src/github.com/skycoin
###### Obtain Skywire source files from Github using GIT
git clone https://github.com/skycoin/skywire.git
###### Chaning into installation path
cd $GOPATH/src/github.com/skycoin/skywire/cmd
###### Run Skywire installation
go install ./...
echo "Skywire succesfully installed!"

##### Now Lauching Skywire

echo "Now lauching Skywire"
cd $GOPATH/bin
./manager -web-dir ${GOPATH}/src/github.com/skycoin/skywire/static/skywire-manager > /dev/null 2>&1 &
echo "Skywire is now running in the background. You can now access the Skywire Manager via the web browser" 
sleep 5
 
##### START THE SKYWIRE NODE
cd $GOPATH/bin 
./node -connect-manager -manager-address 192.168.0.114:5998 -manager-web 192.168.0.114:8000  -address :5000 -web-port :6001 > /dev/null 2>&1 &
echo "Your node is now fully operational and you can see it in the Skywire Manager" 
 
#####################################################################   !!!!! SUPPORT FOR AUTOSTART SERVICES GOES HERE !!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! ########
