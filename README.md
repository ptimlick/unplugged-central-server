# Unplugged Central Server Project
An extension of [ODK Central](www.getodk.org)
A server that can be deployed in challenging emergencies by non experts to facilitate data gathering.
Data from remote wifi connected data gathering devices can be aggregated for backup, analysis and transfer to internet connected servers.
## Goals
  * Internet connection not required
  * Runs on Linux laptop
  * Resiliency in unreliable power environment
  * Wifi Connectivity with Transport Layer Security (TLS) for portable data entry devices
  * full functionality of odk-central on laptop
  * minimal configuration: Install Docker and load Docker archive
  * use existing mechanisms to transfer data to internet
## Outline of implementation
  * TLS security for Wifi connections
    * Create one or more dummy https websites
    * Install full certificate authority chain certificate on unplugged server
    * data entry devices connect through wifi server by dummy name
    * a configuration of odk-central project released as a docker archive
  * Create a wireless access point using https://hub.docker.com/r/offlinehacker/docker-ap
    *  Connects wireless clients to host laptop
    * Installation checks that wireless adapter supports host mode.
    * configure to named Docker bridge (below) to connect wireless access point to odk-central
    * convert from run command to docker-compose extension
  * Modify odk-central to replace docker-compose default internal bridge network with a named network
    * Needed for wifi connection (above) with TLS.  
    * Modification of central project
  * Enhance central server tests to run in docker-compose environment
    * Now require a dedicated and configured (i.e. not Docker) server.
    * used to test named Docker network (above)
    * helpful to qualify laptop hardware
    * Modification of central project
  * Configure database services to not lose data after unanticipated shutdowns
