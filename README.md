# Test for the AKS node upgrade

## Problem statement

It is not possible to add node pools to the cluster created with "Availability Set"
nodes. Additionally old cluster may have "basic" load balancer type. 

Both settings are not possible to change without cluster re-creation and migration. However, in the urgent cases it should be possible to change node types without it.

This PoC is intended to test such scenario

## How to

- Create infra with terraform
- Deploy sample app with `kubectl apply -f deployment.yaml`, wait for load balancer to appear
- drain/cordon first node and upgrade it to another type using azure ui. uncordon
- do same with 2nd node
- check that app is still alive and well

