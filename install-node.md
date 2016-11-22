# Out with the old
First type `which node && which npm` if you get anything other than a blank line you already have node installed and need to remove it. *If you installed node with homebrew or another package manager, use that same package manager to remove your current version of node*. If you used the node installer from their website use these commands:
```
sudo rm -rf $(which node)
sudo rm -rf $(which npm)
sudo rm -rf ~/.node
sudo rm -rf ~/.npm
```
Now if you type `which node && which npm` you should have a blank line.

# In with the new
These instructions will help you install the latest version of node in a way the prevents you from needing root to install
global packages. *You will need curl, python v2.x a C compiler(gcc or clang) and make installed, OSX users will need to make sure they have the latest version of xcode installed and have accepted the user agreement by opening xcode and agreeing to the agreeable agreement*. These can be obtained through whatever package manager your operating system uses (homebrew on Mac, apt-get on Ubuntu, etc).
```
curl -O http://nodejs.org/dist/v4.4.7/node-v4.4.7.tar.gz
tar xvf node-v4.4.7.tar.gz
cd node-v4.4.7
./configure --prefix=$HOME/.node
make && make install
```
These commands will download the latest stable version of node (currently 4.4.7) configure it to install into a .node folder in your 
home directory and will then compile it from source. Next you need to tell your shell to look for the node command in $HOME/.node/bin
On Linux:
```
echo "export PATH=$HOME/.node/bin:$PATH" >> ~/.bashrc
echo "export NODE_PATH=$HOME/.node/lib/node_modules" >> ~/.bashrc
source ~/.bashrc
```
On Mac:
```
echo "export PATH=$HOME/.node/bin:$PATH" >> ~/.bash_profile
echo "export NODE_PATH=$HOME/.node/lib/node_modules" >> ~/.bash_profile
source ~/.bash_profile
```
If you now enter the command `node --version` you should see `v4.4.7`