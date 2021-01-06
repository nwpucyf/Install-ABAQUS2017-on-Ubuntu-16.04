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

