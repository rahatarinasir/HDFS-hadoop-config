hdfs config:

hdfs namenode -format
start-dfs.sh
192.168.56.2:9870
you must see hdfs hadoop
-------------------

my computer---->c---->windows---->system32----->drivers---->etc--->hosts
open host
192.168.56.2 node-master
192.168.56.3 node1
-----------------------
node-master:9870
------------------------
stop-dfs.sh


^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
config YARN hadoop
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
/opt/hadoop-3.2.1/etc/hadoop/
yarn-site.xml

<configuration>

 <property>
    <name>yarn.resourcemanager.hostname</name>
    <value>node-master</value>
  </property>
  
  
<property>
     <name>yarn.nodemanager.resource.memory-mb</name>
     <value>1536</value>
</property>


<property>
     <name>yarn.scheduler.maximum-allocation-mb</name>
     <value>1536</value>
     
     <description>Maximum limit of memory to allocate to each container request at the Resource Manager.</description>
     
</property>



<property>
     <name>yarn.scheduler.minimum-allocation-mb</name>
     <value>512</value>
     <description>Minimum limit of memory to allocate to each container request at the Resource Manager.</description>
     
</property>



 <property>

        <name>yarn.nodemanager.aux-services</name>

        <value>mapreduce_shuffle</value>
        

    </property>
    
    
     <property>

        <name>yarn.nodemanager.vmem-chech-enable</name>

        <value>false</value>

        <description>turn off virtual memory.</description>
    </property>
   
    
    <property>

        <name>yarn.acl.enable</name>

        <value>0</value>
         <description>turn off acl.</description>

    </property>
    
   


</configuration>
----------------------------------------
scp /opt/hadoop-3.2.1/etc/hadoop/yarn-site.xml node1:/opt/hadoop-3.2.1/etc/hadoop/yarn-site.xml

 and copy to another node.
