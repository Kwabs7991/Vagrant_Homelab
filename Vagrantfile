Vagrant.configure("2") do |config|

	# Linux 1 ->> CentOS User Machine -> LON-CENTOS-V001
	config.vm.define "LON-V001" do |lcv1|
	  lcv1.vm.box = "centos/7"
	  lcv1.vm.box_check_update = true
	  lcv1.vm.hostname = "LON-V001"
	  
	  lcv1.vm.network "forwarded_port", guest:80, host:8080
	  lcv1.vm.network "private_network", ip: "192.168.1.10", virtualbox__intnet: "labnetwork1"
	  
	  lcv1.vm.provider "virtualbox" do |vb|
	      vb.memory = "2048"
	      vb.gui = true
	      vb.name = "LON-V001"
	  end

          lcv1.vm.provision "shell", inline: <<-SHELL
            sudo yum update
            sudo yum install net-tools -y
            yum install -y httpd
          SHELL
	end

	
	# Linux 2 ->> CentOS Web Database Server
	config.vm.define "WebDB01" do |web|
          web.vm.box = "centos/7"
          web.vm.box_check_update = true
	  web.vm.hostname = "WebDB01"
          

          web.vm.network "forwarded_port", guest:82, host:8282
          web.vm.network "private_network", ip: "192.168.1.11", virtualbox__intnet: "labnetwork1"


          web.vm.provider "virtualbox" do |vb|
              vb.memory = "2048"
	      vb.gui = false
              vb.name = "WebDB01"
          end
	  
	  web.vm.provision "shell", inline: <<-SHELL
	    sudo yum update
	    sudo yum install net-tools -y
	    yum install -y httpd
	  SHELL
        end



	# Linux 3 ->> CentOS Web Wordpress Server
        config.vm.define "WebServ01" do |wb|
          wb.vm.box = "centos/7"
          wb.vm.box_check_update = true
	  wb.vm.hostname = "WebServ01"
          
          wb.vm.network "forwarded_port", guest:83, host:8383
          wb.vm.network "private_network", ip: "192.168.1.12", virtualbox__intnet: "labnetwork1"


          wb.vm.provider "virtualbox" do |vb|
              vb.memory = "2048"
              vb.gui = false
              vb.name = "WebServ01"
          end

          wb.vm.provision "shell", inline: <<-SHELL
            sudo yum update
            sudo yum install net-tools -y
            yum install -y httpd
          SHELL
        end


	# Linux 4 ->> Ubuntu Web Wordpress Server
        config.vm.define "LON-V002" do |lcv2|
          lcv2.vm.box = "ubuntu/trusty64"
          lcv2.vm.box_check_update = true
	  lcv2.vm.hostname = "LON-V002"

          lcv2.vm.network "forwarded_port", guest:84, host:8484
          lcv2.vm.network "private_network", ip: "192.168.1.13", virtualbox__intnet: "labnetwork1"


          lcv2.vm.provider "virtualbox" do |vb|
              vb.memory = "2048"
              vb.gui = false
              vb.name = "LON-V002"
          end

          lcv2.vm.provision "shell", inline: <<-SHELL
	    sudo apt-get update
            sudo apt install net-tools 
	    sudo apt install apache2
	    sudo apt-get install -y git
          SHELL
        end



##########################################################################

	# Windows Server 2022 1 ->> DNS Server (DC)
        config.vm.define "DNS01" do |dns1|
          dns1.vm.box = "gusztavvargadr/windows-server"
	  dns1.vm.box_check_update = true
          dns1.vm.hostname = "DNS01"

          dns1.vm.network "forwarded_port", guest:85, host:8585
          dns1.vm.network "private_network", ip: "192.168.1.14", virtualbox__intnet: "labnetwork1"

          dns1.vm.provider "virtualbox" do |vb|
              vb.memory = "2048"
              vb.gui = true
              vb.name = "DNS01"
          end
        end


	# Windows Server 2019 1 ->> Email Server 
        config.vm.define "SMTP01" do |smtp1|
          smtp1.vm.box = "StefanScherer/windows_2019"
	  smtp1.vm.box_check_update = true
          smtp1.vm.hostname = "SMTP01"
	  smtp1.winrm.timeout =   1800 # 30 minutes
	  smtp1.vm.boot_timeout = 1800 # 30 minutes
          smtp1.vm.network "forwarded_port", guest:86, host:8686
          smtp1.vm.network "private_network", ip: "192.168.1.15", virtualbox__intnet: "labnetwork1"

          smtp1.vm.provider "virtualbox" do |vb|
              vb.memory = "2048"
              vb.gui = true
              vb.name = "SMTP01"
          end
        end



	# Windows SQL Server 2019 2 ->> SQL Database Server
        config.vm.define "SQL01" do |sql1|
          sql1.vm.box = "gusztavvargadr/sql-server"
	  sql1.vm.box_check_update = true
          sql1.vm.hostname = "SQL01"

          sql1.vm.network "forwarded_port", guest:87, host:8787
          sql1.vm.network "private_network", ip: "192.168.1.16", virtualbox__intnet: "labnetwork1"

          sql1.vm.provider "virtualbox" do |vb|
              vb.memory = "2048"
              vb.gui = true
              vb.name = "SQL01"
          end
        end



	# Windows10 1 ->> User Windows VM
        config.vm.define "LON-V003" do |lvc3|
          lvc3.vm.box = "gusztavvargadr/windows-10"
	  lvc3.vm.box_check_update = true
          lvc3.vm.hostname = "LON-V003"
          
          lvc3.vm.network "forwarded_port", guest:88, host:8888
          lvc3.vm.network "private_network", ip: "192.168.1.17", virtualbox__intnet: "labnetwork1"

          lvc3.vm.provider "virtualbox" do |vb|
              vb.memory = "2048"
              vb.gui = true
              vb.name = "LON-V003"
          end
        end

end

	
