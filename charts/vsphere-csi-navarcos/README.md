# vSphere Container Storage Interface (CSI)

## Checklist

- [ ] ControlPlane nodes must reach vCenter
- [ ] Worker nodes must reach vCenter
- [ ] VM Hardware >=15
- [ ] Primary disk = Paravirtual SCSI controller
- [ ] `disk.EnableUUID=1` on each node VM (default)

## Helm Install

Namespace **MUST** be `vmware-system-csi`

```yaml
helm upgrade vmware-csi --wait --install --namespace vmware-system-csi --create-namespace navarcos/vmware-csi
```

## Original template

The original template is sourced from 

<https://github.com/kubernetes-sigs/vsphere-csi-driver/tree/VERSION/manifests/vanilla>

## vSphere CSI Driver Official Docs

<https://docs.vmware.com/en/VMware-vSphere-Container-Storage-Plug-in/index.html>
