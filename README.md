# Install-ABAQUS2017-on-Ubuntu-16.04

## Pre-requisities for installation  

1.sudo apt-get install csh tcsh ksh libstdc++5 gfortran python-pip libjpeg62 lsb-core libxm4  

2.Install JDK :   

I. sudo mkdir /java  

II. download Java SE Development Kit 15 Downloads/https://www.oracle.com/in/java/technologies/javase-jdk15-downloads.html/  

III. sudo mv ./jdk-15.0.1_linux-x64_bin.tar.gz /java  

IV. sudo tar zxpf ./jdk-15.0.1_linux-x64_bin.tar.gz  

V. sudo gedit ~/.bashrc and add：     


export JAVA_HOME=/java/jdk-15.0.1  

export CLASSPATH=.:$JAVA_HOME/lib:$JAVA_HOME/jre/lib:$CLASSPATH  

export PATH=$JAVA_HOME/bin:$JAVA_HOME/jre/bin:$PATH    


VI:source ~/.bashrc and java -version

## Start the license

1.Remove old SSQ SIMULIA FlexLM servers

2.sudo mkdir /opt/DassaultSystemes

3.sudo tar zxvf ./DS.SIMULIA.FLEXLM.LICENSE.SERVER.LINUX64-SSQ.tar.gz -C /opt/DassaultSystemes

4.Rename  ABAQUSLM_SSQllic as ABAQUS.lic and change the this_host into "hostname" of the computer

5./opt/DassaultSystemes/SIMULIA/License/lmgrd -c /opt/DassaultSystemes/SIMULIA/License/ABAQUS.lic

6.If we want kill the license server, we can use  killall -9 ABAQUSLM

## Install the SIMULIA Suite (Documentation + Simulation Services + ABAQUS/CAE)

### Start

1.Unpack the .iso file

2.find all the Linux.sh files

3.open Linux.sh with VIM (I. Insert mode; II. change DSY_OS_Release=`lsb_release --short --id |sed 's/ //g'` into DSY_OS_Release="CentOS"; III. w !sudo tee %)

2.cd ./1/

3.export DSYAuthOS_`lsb_release -si`=1 && export DSY_Force_OS=linux_a64 && sudo ksh ./StartGUI.sh

4.Do not install FLEXNET license server!!!

### Install Documentation

1.Select directory "/opt/DassaultSystemes/SIMULIA2017doc/"

2.Continue Next until step is complete

### Install Simulation Services and CAA API

1.Select installation directory "/opt/DassaultSystemes/SimulationServices/V6R2017x"

3.Select components (by default, all components are selected)

3.Continue Next until step is complete

### Install ABAQUS/CAE

1.Select installation directory "/opt/DassaultSystemes/SIMULIA/CAE/2017"

2.Select Simulation Services directory "/opt/DassaultSystemes/SimulationServices/V6R2017x"

3.Select commands directory "/opt/DassaultSystemes/SIMULIA/Commands/"

4.Select ABAQUS/CAE External plugins directory "/opt/DassaultSystemes/SIMULIA/CAE/plugins/2017"

5.Select "SIMULIA FlexNET Licensing" and "27011@hostname" as License Server 1

6.Select "enter a file path to documentation directory" and point to directory "/opt/DassaultSystemes/SIMULIA2017doc/"

7.Continue Next until step is complete

## Open ABAQUS

XLIB_SKIP_ARGB_VISUALS=1 /opt/DassaultSystemes/SIMULIA/Commands/abq2017 cae -mesa

Or

gedit ~/.bashrc  and add 

export LM_LICENSE_FILE=27011@cyf-virtual-machine
alias abalic=/opt/DassaultSystemes/SIMULIA/License/lmgrd\ -c\ /opt/DassaultSystemes/SIMULIA/License/ABAQUS.lic\ -l\ +/opt/DassaultSystemes/SIMULIA/License/ABAQUS.log
alias abaqus='XLIB_SKIP_ARGB_VISUALS=1 /opt/DassaultSystemes/SIMULIA/Commands/abq2017'
alias cae='abaqus cae -mesa'

then source ~/.bashrc

