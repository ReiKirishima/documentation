---
title: "MinIO Plugin"
description: "Describes how to configure the MinIO plugin on TrueNAS CORE and gives migration instructions from the deprecated S3 built-in service."
weight: 20
tags:
- coreplugins
- corejailspluginsvm
- cores3
- minio
---

{{< toc >}}

The **Minio** official plugin from the iXsystems catalog is a High-performance object (S3) storage suite, natively available on TrueNAS CORE.

{{< expand "Background" "v" >}}
S3 is an object storage protocol used by many major cloud providers, including Amazon Web Services™. You can view these files with a web browser. S3 is the de facto standard for cloud-based storage. Organizations or online application developers can use TrueNAS with the **Minio** plugin to manage S3 storage. This can replace or archive expensive cloud storage.
{{< /expand >}}

This tutorial describes how to install the **Minio** plugin on TrueNAS.

{{< expand "S3 Service Deprecation and Migration" "v" >}}
{{< include file="/_includes/S3Deprecation.md" >}}

The TrueNAS S3 service is based on version 2021-11-24T23:19:33Z and utilizes MinIO Filesystem/Gateway mode. Filesystem/Gateway mode is deprecated, beginning with MinIO version RELEASE.2022-10-24T18-35-07Z. Newer deployments of MinIO are unable to access data from the TrueNAS S3 service.

The MinIO client provides provisions for properly migrating and converting MinIO data stored in buckets. However, all configuration data must be migrated by manually recreating users, policies, buckets, and other resources on the new deployment.

For additional information please review [Migrate from Gateway or Filesystem Mode](https://min.io/docs/minio/container/operations/install-deploy-manage/migrate-fs-gateway.html) on the MinIO Documentation hub.
{{< /expand >}}

## First Steps

[Create a dataset]({{< relref "CORE/CORETutorials/Storage/Pools/Datasets.md" >}}) to use for **Minio** Plugin storage.
MinIO manages files as objects.
These objects cannot mix with other dataset files.

In order to migrate data from an existing S3 service deployment running on TrueNAS CORE, the new destination dataset must have available storage capacity at least equal to the existing S3 service configuration.
Data can be migrated to a different networked device with enough storage capacity, however transfer rates may be slower depending on network configuration.

For better performance, total pool capacity should not exceed 80%.
For example, if the original S3 dataset is 25TB and the destination dataset is created in the same pool, the total pool capacity should be at least 62.5TB (25TB for each dataset plus 20% overhead).

## Installing the Minio Plugin

Go to the **Plugins** screen.
If you have not previously configured plugins on the system, follow the initial setup instructions in [Managing Plugins]({{< relref "ManagingPlugins.md" >}}).

{{< trueimage src="images/CORE/Plugins/MinioPluginDetails.png" alt="Minio Plugin Details Screen" id="Minio Plugin Details Screen" >}}

Select the **Minio** plugin from the iXsystems collection.
Click **INSTALL**.

{{< trueimage src="images/CORE/Plugins/MinioPluginInstall.png" alt="Install Minio Plugin" id="Install Minio Plugin" >}}

Enter a name for the plugin in **Jail Name** and adjust the networking settings as needed.
You can use the default [Network Address Translation (**NAT**)](https://datatracker.ietf.org/wg/nat/about/), enable **DHCP**, or manually define IP addresses.

{{< hint type=tip >}}
If migrating data from an existing S3 service deployment, ensure ports for the **Minio** plugin are different from the existing service.

{{< /hint >}}

Click **Save** to install.
A dialog confirms when the installation completes and shows post-install notes, including the `MINIO_ACCESS_KEY` and `MINIO_SECRET_KEY`.
You can view the post-install notes later by expanding the entry for the installed plugin in **Plugins** and clicking <i class="fa fa-file-alt" aria-hidden="true" title="File"></i> **Post Install Notes**.

The **Plugins** screen shows the installed plugin.

{{< trueimage src="images/CORE/Plugins/MinioPluginInstalled.png" alt="Minio Plugin Installed" id="Minio Plugin Installed" >}}

Click <i class="material-icons" aria-hidden="true" title="Expand">chevron_right</i> to expand the **Minio** plugin details and management options.
Click <i class="fa fa-stop" aria-hidden="true" title="Stop"></i>&nbsp;**STOP** to stop the jail before making any changes.

Click <span class="material-icons">device_hub</span>&nbsp;**MOUNT POINTS** and follow the instructions in [Setting Up Jail Storage]({{< relref "SettingUpJailStorage.md" >}}) to mount the destination dataset you created in [First Steps](#first-steps).

Click <span class="material-icons">play_arrow</span>&nbsp;**START** to restart the plugin and then click <span class="material-icons">settings</span>&nbsp;**MANAGE** to go to the **MinIO Console** and log in.

{{< trueimage src="images/CORE/Plugins/MinioPluginConsole.png" alt="MinIO Console" id="MinIO Console" >}}