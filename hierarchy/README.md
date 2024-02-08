# HW1 Submission
In this Homework we had to study the memory and storage hierarchy in the data center <br />
**For this assignment i selected The CloudLab cluster at the University of Wisconsin** <br />
The 2 nodes i used was type **c220g5** with the following characteristics :
  * CPU : Two Intel Xeon Silver 4114 10-core CPUs at 2.20 GHz
  * RAM : 192GB ECC DDR4-2666 Memory
  * Disk : One 1 TB 7200 RPM 6G SAS HDs
  * Disk : One Intel DC S3500 480 GB 6G SATA SSD
  * GPU : One NVIDIA 12GB PCI P100 GPU

## Comments on the results 

### Gapicity (GB)
Since we have 2 identical nodes of type **c220g5** the have the same campacities :
 1. Local DRAM : 187 GB
 2. Local Disk : 480 GB
Because we are not able to know how many nodes we have in each rack we can't calculate the Remote Capacity of DRAM and DISK so in the graph is set to the value of Local DRAM and Local Disk .

### Latency (us)
The analysis of the graph clearly indicates that Local DRAM exhibits the lowest latency, recorded at a mere 0.0915 microseconds (us). This is in line with expectations given the inherent efficiency of Local DRAM. On the other hand, the latency of the Local Disk is significantly higher, at 247 us, which, while expected for Local Disk performance, is noteworthy. Upon further research, it was found that the One Intel DC S3500 480 GB 6G SATA SSD typically maintains low read latencies around 50us, only reaching a maximum of 500us in 99.9% of cases. This observation underscores the remarkable data reading efficiency of this disk.<br />
In examining Remote Latency, both for DRAM and Disk, the calculations incorporated the network’s latency, which was determined to be 51 us. By adding this network latency to the respective Local DRAM and Local Disk latencies, the Remote DRAM latency was calculated at 51.09 us, and the Remote Disk latency at 298 us. From these findings, it is evident that the highest latency is exhibited by the Remote Disk, while the lowest latency is observed in the Local DRAM, aligning with initial expectations.

### Bandwidth(MB/s)
In our analysis of bandwidth, we anticipated high speeds for Local DRAM, which was indeed confirmed with an impressive rate of approximately 49011 MB/s, or equivalently around 48 GB/s. For the Local Disk, the measured bandwidth was determined to be 276 MB/s.<br />
When calculating the Network Bandwidth, we found it to be 428 MB/s. This value proved to be the limiting factor for the Remote DRAM Bandwidth. However, for the Remote Disk Bandwidth, the bottleneck was identified as the Local Disk Bandwidth, which resulted in a capped bandwidth of 276 MB/s for the Remote Disk.

## Conclusion
The findings from our analysis lead to a noteworthy conclusion regarding the efficiency of accessing remote DRAM compared to local disk storage. It is evident that reaching out to remote DRAM is more advantageous, as it offers higher bandwidths, with the network bandwidth (428 MB/s) being the limiting factor. This bandwidth is significantly greater than that of the Local Disk, which is capped at 276 MB/s.<br />
Additionally, the latency aspect further supports this preference. The latency involved in accessing remote DRAM, even when factoring in network delays, is still less than that of accessing local disk storage. This combination of higher bandwidth and lower latency makes remote DRAM a more efficient choice for data access compared to relying on local disk resources.


![image](https://github.com/ucy-cs452-sp24/hw1-GeorgeChorattas/blob/main/hierarchy/measures_graph.png?raw=true)




