---
title: Prepare Linux for Cache Volumes (preview) using a single-node or two-node cluster
description: Learn how to prepare Linux for Cache Volumes with a single-node or two-node cluster in Azure Container Storage enabled by Azure Arc using AKS enabled by Azure Arc, Edge Essentials, or Ubuntu.
author: asergaz
ms.author: sergaz
ms.topic: how-to
ms.custom: linux-related-content
ms.date: 03/12/2025
zone_pivot_groups: platform-select
---

# Prepare Linux for Cache Volumes (preview) using a single-node or two-node cluster

This article describes how to prepare Linux using a single-node or two-node cluster, and assumes you [fulfilled the prerequisites](prepare-linux.md#prerequisites).

::: zone pivot="aks"
## Prepare Linux with AKS enabled by Azure Arc

This section describes how to prepare Linux with AKS enabled by Azure Arc if you run a single-node or two-node cluster.

- Disable **ACStor** by creating a file named **config.json** with the following contents:

   ```json
   {
     "feature.diskStorageClass": "default",
     "acstorController.enabled": false
   }
   ```

::: zone-end

::: zone pivot="aks-ee"
[!INCLUDE [single-node-ee](includes/single-node-edge-essentials.md)]

4. Disable **ACStor** by creating a file named **config.json** with the following contents:

   ```json
   {
     "acstorController.enabled": false,
     "feature.diskStorageClass": "local-path"
   }
   ```

::: zone-end

::: zone pivot="ubuntu"
[!INCLUDE [single-node-ubuntu](includes/single-node-ubuntu.md)]

2. Disable **ACStor** by creating a file named **config.json** with the following contents:

   ```json
   {
     "acstorController.enabled": false,
     "feature.diskStorageClass": "local-path"
   }
   ```

::: zone-end

## Next steps

[Install Azure Container Storage enabled by Azure Arc Cache Volumes (preview)](install-cache-volumes.md)
