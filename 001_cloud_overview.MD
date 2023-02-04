# Cloud Overview
## In order for largest to smallest     
Regions    
Availability Zones    
Local Zones   

Regions - Global locations in specfic countries.  Some countries have multiple regions (e.g., the US)   

Availability Zones - Inside of a region are availability zones. They are descrete data centers, w/redundant power, interconnected, low-latency network, pyhsically separated, encrypted. They are identified like region us-east-1. A min of 2, max of 6 per region

Local Zones - AWS Local Zones are a type of AWS infrastructure deployment that place compute, storage, database, and other select services closer to large population, industry, and IT centers, enabling you to deliver applications that require single-digit millisecond latency to end-users.  These are an extension of a region and are used for latency sensitive applications (e.g., games, machine learning).   

How to pick a region? Legal compliance per country. Proximity to customers. Available services (e.g., not all regions have the same services).  Pricing as it varies from region to region.