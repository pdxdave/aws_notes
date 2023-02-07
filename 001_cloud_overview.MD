# Cloud Overview
## In order for largest to smallest     
Regions    
Availability Zones    
Local Zones  
Edge Zones
Wavelength 

Regions - Global locations in specfic countries.  Some countries have multiple regions (e.g., the US).  Regions have clusters of data centers.  They are identified like region us-east-1, eu-central-1.

Availability Zones - Each logical data center is an Availability Zone. They are descrete data centers, w/redundant power, are interconnected, have low-latency network, are pyhsically separated, and encrypted. . There are a min of 2, max of 6 per region. If there are two in us-east-1, they would be id'd as us-east-1a, us-east-1b.

Local Zones - AWS Local Zones are a type of AWS infrastructure deployment that place computing, storage, databases, and other select services ```closer to large population```, industry, and IT centers, enabling you to deliver applications that require single-digit millisecond latency to end-users.  These are an extension of a region and are used for latency sensitive applications (e.g., games, machine learning).   

Edge Locations - These are end points for AWS. They cache content and are used as CDNs. 

```How to choose an AWS region?``` Legal compliance per country. Proximity to customers. Available services (e.g., not all regions have the same services).  Pricing as it varies from region to region.    

Wavelength - enables developers to build applications that deliver single-digit millisecond latencies to mobile devices and end-users.