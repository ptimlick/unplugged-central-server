# Unplugged Central Server Project
An extension of [ODK Central](www.getodk.org)
A server that can be deployed in challenging emergencies by non experts to facilitate data gathering. 
Data from android gathering devices can be aggregated for backup, analysis and transfer to internet connected servers. 
## Goals
  * Internet connection not required
  * Moderately endowed Linux Laptop
  * Wifi Connectivity with TLS Security for standard Android devices
  * full functionality of odk server on laptop
  * use existing mechanisms to transfer data to internet 
## Outline of implementation
  * Unplugged TLS security for Android-Wifi connections
    * Create one or more dummy https websites
    * Install full certificate authority chain certificate on unplugged server
    * Android phones connect through wifi server by dummy name
    * a configuration of odk-central project released as a docker archive
  * create a wireless access point using https://hub.docker.com/r/offlinehacker/docker-ap
    * now bridges wireless clients to host connected internet
    * configure to bridge to odk-central running on host laptop
    * convert from run command to docker-compose extension
  * Modify odk-central to replace default internal bridge network with a named network
    * Needed for TLS Security of the wifi connection (above).  
    * Docker-compose "best practice"
    * Modification of central project
  * Enhance central server tests to run in docker-compose environment
    * Now require a dedicated and configured (i.e. not docker) server.
    * used to test named network (above)
    * helpful to qualify laptop hardware
    * Modification of central project
