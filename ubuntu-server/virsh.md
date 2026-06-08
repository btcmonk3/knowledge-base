# Managing Libvirt Virtual Machines via virsh

Use the following `virsh` commands to check the status of virtual machines.

### Show Running VMs:

- Display a list of currently active machines, incl. their ID, name, and state.

```bash
virsh list
```

### Show All VMs

- Displays a list of ALL machines on the host, including stopped, suspended, or inactive.

```bash
virsh list --all
```

### Start a VM

- Power on an inactive, defined virtual machine.

```bash
virsh start <vm-name>
```

### Gracefully Shutdown a VM:

- Sends an ACPI shutdown signal to the guest operating system, triggering a clean system halt.

```bash
virsh shutdown <vm-name>
```

### Suspend (Pause) a VM:

```bash
virsh suspend <vm-name>
```

### Resume a VM:

```bash
virsh resume <vm-name>
```

### Force stop a VM:

- Pulls the virtual "power plug". Does not delete any data.

```bash
virsh destroy <vm-name>
```

### Remove a VM Configuration:

- Delete a VM definition but leave the virtual disk file in place /var/lib/libvirt/images.

```bash
virsh undefine <vm-name>
```

### Purge a VM and remove its storage completely:

- Delete a VM definition but leave the virtual disk file in place /var/lib/libvirt/images.

```bash
virsh undefine <vm-name>
```

Use `virsh domblklist <vm-name>~` first to find the exact storage target name, usually `vda` or `hda`).

The default directory for disk files is `/var/lib/libvirt/images`
