Atitit geckodriver linux安装


ere are the steps:

Go to the geckodriver releases page. Find the latest version of the driver for your platform and download it. For example:

wget https://github.com/mozilla/geckodriver/releases/download/v0.24.0/geckodriver-v0.24.0-linux64.tar.gz


Extract the file with:

tar -xvzf geckodriver*


Make it executable:

chmod +x geckodriver


Add the driver to your PATH so other tools can find it:

export PATH=$PATH:/path-to-extracted-file/.


