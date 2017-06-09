Canary Deployment Demonstration for Openshift
=============================================
Canary release is a technique to reduce the risk of introducing a new software version in production by slowly rolling out the change to a small subset of users before rolling it out to the entire infrastructure and making it available to everybody.

There are different strategies to choose which users will see the new version: a simple strategy is to use a random sample; some companies choose to release the new version to their internal users and employees before releasing to the world; another more sophisticated approach is to choose users based on their profile and other demographics.

This demo shows how to implement canary deploy using customized haproxy acl

1. deploy the stable version and new version two environments
2. customize haproxy-config.template
3. release the new version to the specified ip