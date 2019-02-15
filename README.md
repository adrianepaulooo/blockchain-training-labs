# blockchain-training-labs


Laptop Specifications

Device: Laptop
OS: Ubuntu 18.04.1 LTS
System Type: 64-bit
Processor: Intel® Core™ i3-6100U CPU @ 2.30GHz × 4
Ram: 4GB

Before you proceed to Hyperledger Composer Prerequisites installation, you need to install Node and Docker as one of the 
requirements in Hyperledger.

Node --	https://nodejs.org/en/download/package-manager/#debian-and-ubuntu-based-linux-distributions
Docker --https://medium.com/@sebagomez/installing-the-docker-client-on-ubuntus-windows-subsystem-for-linux-612b392a44c4

Hyperledger Prerequisites Installation

Open a Terminal, then enter the following command.

curl –O https://hyperledger.github.io/composer/latest/prereqs-ubuntu.sh
chmod u+x prereqs-ubuntu.sh
./prereqs-ubuntu.sh

After that, install Go language using this command.

wget https://storage.googleapis.com/golang/go1.9.2.linux-amd64.tar.gz && \


sudo tar -C /usr/local -xzf go1.9.2.linux-amd64.tar.gz && \
rm go1.9.2.linux-amd64.tar.gz && \
echo 'export PATH=$PATH:/usr/local/go/bin' | sudo tee -a /etc/profile && \
echo 'export GOPATH=$HOME/go' | tee -a $HOME/.bashrc && \
echo 'export PATH=$PATH:$GOROOT/bin:$GOPATH/bin' | tee -a $HOME/.bashrc && \
mkdir -p $HOME/go/{src,pkg,bin}


You can check your Go language version using terminal by typing this command: 
go version

Then install vscode using terminal by typing this command:
sudo snap install vscode –classic

After installing the vscode, Open the application the go to View > Extension (CTRL + SHIFT + X) And search Hyperledger Composer 
in the search bar then install it.


    Activity


    Clone the repositories using terminal by typing this command:
    git clone https://github.com/adrianepaulooo/blockchain-training-labs/
    git clone https://github.com/hyperledger/fabric-samples/

    1. Open the blockchain-training-labs folder then go to chaincode folder and copy the supply folder.
    
    2. Go to fabric-samples folder then go to chaincode folder and paste the file you copied.
    
    3. Open the blockchain-training-labs folder then copy the supply folder.
    
    4. Go back to fabric-samples folder and paste the file you copied.
    
    5. Download all the required library for our the following commands
    
	go get github.com/golang/protobuf/proto
	go get github.com/hyperledger/fabric/common/attrmgr
	go get github.com/pkg/errors
	go get github.com/hyperledger/fabric/core/chaincode/lib/cid
	
	Open file manager go to Home > go > src > github.com then copy and paste all the folders in fabric-samples > chaincode 

    6. In the fabric-samples > supply open a Terminal, then type 
       ./startFabric.sh
       Then type npm install, if you this line after installing node-pre-gyp WARN Using request for node-pre-gyp https download.
       Press Ctrl+C.

    7. node enrollAdmin.js 

    8. node registerSupplier.js

    9. node registerOEM.js

    10. node registerBank.js

    11. node app.js

    12. To POST data, select POST and type http://localhost:3000/invoice/ 
        Click Headers then add KEY = user  and VALUE = supplier 
        Switch to Body > select x-www-form-urlencoded and click Bulk Edit to paste this as example 	data:

      	invoicenumber:INVOICE001
      	billedto:OEM
      	invoicedate:02/08/19
      	invoiceamount:10000
      	itemdescription:KEYBOARD
      	goodreceived:False
      	ispaid:False
      	paidamount:0
      	repaid:False
      	repaymentamount:0

      	then click Send button.
      	To see you invoice, select Get  and type http://localhost:3000/
      	Click Headers then add KEY = user  and VALUE = supplier.

    13. Declaring Good Recieved
       To EDIT data, select PUT and type http://localhost:3000/invoice/ then go to Header and input this data.  KEY = user  and 
       VALUE = oem
       Switch to Body > select x-www-form-urlencoded  and  input all these data 
       invoicenumber = INVOICE001 and goodrecieved = True.
       Then click Send button.
    
    14.  Bank will pay the supplier 
       Select PUT and type http://localhost:3000/invoice/ then go to Header and input this data.  KEY = user  and VALUE = bank
       Switch to Body > select x-www-form-urlencoded  and  input all these data 
       invoicenumber = INVOICE001 and paidamount 9000.
       Then click Send button.
       To check if the data is already updated, select GET and type http://localhost:3000/ then click Send.

    15.  Oem will pay the bank
       Select PUT and type http://localhost:3000/invoice/ then go to Header and input this data.  KEY = user  and VALUE = oem
       Switch to Body > select x-www-form-urlencoded  and  input all these data 
       invoicenumber = INVOICE001 and repaymentamount = 11000.
       Then click Send button.
       To check if the data is already updated, select GET and type http://localhost:3000/ then click Send. 

    16. Checking invoice trail
       Select GET and type http://localhost:3000/ then go to Header and input this data.  KEY = user  and VALUE = supplier
       Switch to Body > select x-www-form-urlencoded  and  input all these data 
       invoicenumber = INVOICE001.
       Then click Send button.

	



       
       



       
       







