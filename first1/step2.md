
# Creating a PV/PVC

The example-voting-app configures a PersistentVolumeClaim (or PVC) for use by the PostgreSQL app.

For this we need to
- Make mult-node??
- Create a physical volume mount directory on the master node
- Create a PersistentVolume on the master node
- Modify the definition of PersistentVolumeClaim in kube-deployment.yml to specify the same storage class

## Creating the data directory

`mkdir /mnt/data`{{copy}}

## Creating the PV

Create a file called *pv.yaml* with the following contents

```yaml
apiVersion: v1
kind: PersistentVolume
metadata:
  name: local-pv
spec:
  capacity:
    storage: 3Gi
  volumeMode: Filesystem
  accessModes:
  - ReadWriteOnce
  persistentVolumeReclaimPolicy: Delete
  storageClassName: local-storage
  hostPath:
    path: "/mnt/data"
```

Now create the PV using command `kubectl create -f pv.yaml`{{copy}}

Verify that the PV is present using
`kubectl get pv`{{copy}},
you should see output similar to

```
NAME       CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS      CLAIM   STORAGECLASS    REASON   AGE
local-pv   3Gi        RWO            Delete           Available           local-storage            1s
```


## Specifying the PVC

Now we must edit the kube-deployment.yml file so that the PersistentVolumeClaim requests storage of class *local-storage* as specified in pv.yaml

Edit the kube-deployment.yml file so that the PersistentVolumeClaim declaration look s like

```yaml
apiVersion: v1
kind: PersistentVolumeClaim
metadata:
  name: postgres-pv-claim
spec:
  accessModes:
    - ReadWriteOnce
  storageClassName: local-storage
  resources:
    requests:
      storage: 1Gi
```




