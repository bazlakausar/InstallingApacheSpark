## InstallingApacheSpark

   1) You must first install the required prerequisites before downloading and installing Spark. 
      The following packages must be installed in this step: Scala, JDK, and Git.
      
           sudo apt install default-jdk scala git -y 
           
       Run the above command to download all three packages.
        
           java -version; javac -version; scala -version; git --version
           
        Run the above command to check the installed dependencies
        
   2) You must now download the version of Spark that you want from their website.
     
           wget https://lcdn.apache.org/spark/spark-3.2.0/spark-3.2.0-bin-hadoop3.2.tgz
          
        Extracting the saved archive:
          
          tar xvf spark-*
          
   3) Finally, copy the spark-3.2.1-bin-hadoop3.2 directory to the opt/spark directory. To do so, use the mv command.
    
           sudo mv spark-3.0.1-bin-hadoop2.7 /opt/spark
           
           
   4) Configuring Spark environment
   
      Let's add the export paths to the.profile file using your preferred editor, such as nano or vim.
         
            nano .profile
            
        Then, add these three lines:

              export SPARK_HOME=/opt/spark

              export PATH=$PATH:$SPARK_HOME/bin:$SPARK_HOME/sbin

              export PYSPARK_PYTHON=/usr/bin/python3

         Exit and save changes when prompted.
         
   5) Starting Spark Master Server
        You may now launch a master server once you've finished setting your Spark environment.
        
               start-master.sh
               
   6) Open a web browser and type the localhost IP address on port 8080 to see the Spark Web user interface.
    
              http://127.0.0.1:8080/
              
              
   7) Starting a Worker Process (Spark Slave Process)
        We'll launch one slave server alongside the master server in this single-server, standalone arrangement.
        To do so, use the command below.
        
              start-slave.sh spark://master:port
              
   8) When launching a worker on a system, the default configuration is to use all available CPU cores. The -c argument to the start-slave command can be used to indicate the number of cores.
   
        When creating a worker, you may also assign a certain amount of RAM.
        Add the -m option and a number to start a worker and allocate it a certain amount of memory. Use G for gigabytes and M for megabytes.
        
              start-slave.sh -c 1 spark://master:port
              start-slave.sh -m 512M spark://master:port
              
       To see the worker's status and validate the setup, reload the Spark Master Web UI.
       
   9) Now, try loading the shell
           
              spark-shell
 
         A screen containing alerts and Spark information should appear. Because Scala is the default interface, when you run spark-shell, the shell loads.
         
         
           
           
           
           
           
           
           
           
           
