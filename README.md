# Snell-Protocol Install On Ubuntu18.04
	About: https://github.com/surge-networks
## Step1:Downlaod File from Github
	$ sudo wget wget https://dl.nssurge.com/snell/snell-server-v4.0.1-linux-amd64.zip
## Step2:Unzip File
 	$ sudo unzip snell-server-v4.0.1-linux-amd64.zip
## Step3:Move File to "/usr/local/bin/"
	$ sudo mv snell-server /usr/local/bin/
## Step4:Create An File "snell.service" in "/etc/systemd/system/"
	$ sudo touch /etc/systemd/system/snell.service
## Step5:Editor "snell.service":
	[Unit]
	Description=Snell Proxy Service
	After=network.target

	[Service]
	Type=simple
	LimitNOFILE=32768
	ExecStart=/usr/local/bin/snell-server -c /etc/snell/snell-server.conf

	[Install]
	WantedBy=multi-user.target
## Step6:Create An File "snell-server.conf" in "/etc/snell/"
	$ sudo touch /etc/snell/snell-server.conf
## Step7:Editor "snell-server.conf"
	[snell-server]
	listen = 0.0.0.0:13873	#Listening port
	psk = xxxxxxxxxxxxxx	#your psk
	obfs = tls		#http/tls
## Step8:Start with OS:
	$sudo systemctl daemon-reload  
	$sudo systemctl start snell.service		#Start snell service
	$sudo systemctl enable snell.service		#Enable Start with OS
	$sudo systemctl status snell.service		#snell service status
		
## Step9:Config for "Clash for Windows":
	-name:example  		#Remark
	type:snell
	server:xxx.xxx.xxx.xxx	#your vps addres
	prot:"13281"		#Listening port
	psk:xxxxxxxx		#your psk
	obfs-opts:
		mode:tls
## Links:https://github.com/surge-networks
## enjoy it!

	
  
