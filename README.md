Canary Deployment Demonstration for Openshift
=============================================
Canary release is a technique to reduce the risk of introducing a new software version in production by slowly rolling out the change to a small subset of users before rolling it out to the entire infrastructure and making it available to everybody.

There are different strategies to choose which users will see the new version: a simple strategy is to use a random sample; some companies choose to release the new version to their internal users and employees before releasing to the world; another more sophisticated approach is to choose users based on their profile and other demographics.

This demo shows how to implement canary deployment using customized haproxy acl

* deploy the stable version and new version two environments  
* expose two routes for stable and new version  
* customize haproxy-config.template, add acl to frontend public section, forward traffic to different backends by acl rule filter

  example:  
  acl network_specified src 192.168.137.0/24  
  acl host_specified hdr(host) -i cotd-city.192.168.137.3.nip.io  
  use_backend be_http_cotd_new if host_specified network_specified  
  use_backend be_http_cotd_city if host_specified !network_specified  
  
* use configmap to replace the openshift router configuration template