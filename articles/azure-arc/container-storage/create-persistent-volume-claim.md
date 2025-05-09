---
title: Create a Persistent Volume Claim (PVC)
description: Learn how to create a Persistent Volume Claim (PVC) in Cache Volumes (preview).
author: asergaz
ms.author: sergaz
ms.topic: how-to
ms.date: 09/24/2024

---

# Create a Persistent Volume Claim (PVC)

The PVC is a persistent volume claim against the persistent volume that you can use to mount a Kubernetes pod.

This size does not affect the ceiling of blob storage used in the cloud to support this local cache. Make a note of the name of this PVC, as you need it when you create your application pod.  

## Create PVC

1. Create a file named **pvc.yaml** with the following contents:

   ```yaml
   apiVersion: v1 
   kind: PersistentVolumeClaim 
   metadata:
       ### Create a name for your PVC ###
       name: CREATE_A_NAME_HERE
       ### Use a namespace that matched your intended consuming pod, or "default" ###
       namespace: INTENDED_CONSUMING_POD_OR_DEFAULT_HERE
   spec: 
       accessModes: 
           - ReadWriteMany 
       resources: 
           requests: 
               storage: 5Gi 
       storageClassName: esa
       volumeMode: Filesystem
       ### This name references your PV name in your PV config ###
       volumeName: INSERT_YOUR_PV_NAME
   ```

1. To apply this .yaml file, run:

    ```bash
    kubectl apply -f "pvc.yaml"
    ```

## Next steps

After you create a Persistent Volume Claim (PVC), attach your app (Azure IoT Operations Data Processor or Kubernetes Native Application):

[Attach your app](attach-app.md)
