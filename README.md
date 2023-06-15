# Home-Assistant-on-Kubernetes
Kustomized manifests for running Home Assistant on Kubernetes

Tested on K3s running on AMD64 architecture.

Read the blogpost from subject on [balagetech.com: Running Home Assistant on Kubernetes](https://balagetech.com/running-home-assistant-on-kubernetes)

## Network requirements

This setup requires separate VLANs for IoT devices and your regular network you want to access Home Assistant from.

Should you want to create VLANs but don't know how?  
There is a great video tutorial for creating VLANs on OpenWRT by Marc Ahlgrim. Make sure to check it out.  
[VLANs in OpenWrt 21](https://www.youtube.com/watch?v=qeuZqRqH-ug)

## Adjust deployment settings

The main `kustomization.yaml` holds the environment specific settings.

You can set:
- FQDN of your installation
- Static IP for your Home Assistant (required for accessing by IoT devices as auto-detect will not work)
- Timezone

You may also want to adjust `mosquitto/password_file` by using [mosquitto_passwd](https://mosquitto.org/man/mosquitto_passwd-1.html).

## Install

Assuming you have your kubectl configured to point to your Kubernetes cluster.

```
kubectl apply -k .
```
