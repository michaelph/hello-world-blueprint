[![CircleCI](https://circleci.com/gh/cloudify-examples/hello-world-blueprint.svg?style=svg)](https://circleci.com/gh/cloudify-examples/hello-world-blueprint)

# Cloudify Hello World Example

This blueprint deploys a python webserver that says "hello world", with a cute Cloudify logo.

## Compatibility

Tested with:
  * Cloudify 4.3.1


## Pre-installation steps

**Please note the following requirement for manager configuration.**

This example requires configuration of [multiple management (agent) networks](https://docs.cloudify.co/4.3.0/install_maintain/installation/installing-manager/#multi-network-management) upon installation of your Cloudify Manager.

The required name of the agent network is `external`, and should map to a public IP address. For example:

```bash
[centos@ip-10-10-4-47 ~]$ sudo grep "networks" /etc/cloudify/config.yaml 
    networks: {default: 10.10.4.47, external: 54.67.45.103}
```

Upload the required plugins:

  * [Openstack Plugin](https://github.com/cloudify-cosmo/cloudify-openstack-plugin/releases).
  * [AWSSDK Plugin](https://github.com/cloudify-incubator/cloudify-awssdk-plugin/releases).
  * [AWS Plugin](https://github.com/cloudify-cosmo/cloudify-aws-plugin/releases).
  * [GCP Plugin](https://github.com/cloudify-incubator/cloudify-gcp-plugin/releases).
  * [Azure Plugin](https://github.com/cloudify-incubator/cloudify-azure-plugin/releases).
  * [Utilities Plugin](https://github.com/cloudify-incubator/cloudify-utilities-plugin/releases).

_Check the blueprint for the latest version of the plugin._

Install the relevant example network blueprint for the IaaS that you wish to deploy on:

  * [Openstack Example Network](https://github.com/cloudify-examples/openstack-example-network)
  * [AWS Example Network](https://github.com/cloudify-examples/aws-example-network)
  * [GCP Example Network](https://github.com/cloudify-examples/gcp-example-network)
  * [Azure Example Network](https://github.com/cloudify-examples/azure-example-network)

## Installation

On your Cloudify Manager, navigate to `Local Blueprints` select `Upload`.

[Right-click and copy URL](https://github.com/cloudify-examples/hello-world-blueprint/archive/master.zip). Paste the URL where it says `Enter blueprint url`. Provide a blueprint name, such as `hello-world` in the field labeled `blueprint name`.

Select the blueprint for the relevant IaaS you wish to deploy on, for example `openstack.yaml` from `Blueprint filename` menu. Click `Upload`.

After the new blueprint has been created, click the `Deploy` button.

Navigate to `Deployments`, find your new deployment, select `Install` from the `workflow`'s menu. At this stage, you may provide your own values for any of the default `deployment inputs`.


## Uninstallation

Navigate to the deployment and select `Uninstall`. When the uninstall workflow is finished, select `Delete deployment`.
