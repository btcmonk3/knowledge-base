# Managing KVM/Libvirt Virtual Machines via virsh

The following `virsh` commands are used to control virtual machines.

### List Running VMs

Display a list of all currently active machines, including their ID, name, and state.

```bash
virsh list
```

### List All VMs

Display a list of ALL machines on the host, including stopped, suspended, or inactive.

```bash
virsh list --all
```

### Start a VM

Power on an inactive virtual machine.

```bash
virsh start <vm-name>
```

### Shutdown a VM Gracefully

Send a clean shutdown signal to the OS.

```bash
virsh shutdown <vm-name>
```

### Reboot a VM

Trigger a clean soft-reboot via ACPI within the guest operating system.

```bash
virsh reboot <vm-name>
```

### Suspend (Pause) a VM

Freeze the VM's current execution state in host memory. CPU cycles are freed, but memory remains allocated.

```bash
virsh suspend <vm-name>
```

### Resume (Unpause) a VM

Unfreeze a suspended virtual machine, restore CPU execution instantly.

```bash
virsh resume <vm-name>
```

### Force Stop a VM

Immediately halts the virtual machine by pulling the virtual "power plug".

```bash
virsh destroy <vm-name>
```

- Note: Does not delete any data or configuration files, but can cause filesystem corruption in the OS.

### Purge a VM (Configuration Only)

Delete a VM definition but leave the virtual disk file in place.

```bash
virsh undefine <vm-name>
```

- Note: May need to add additional flags `--nvram --snapshots-metadata`.

### Purge a VM with Complete Storage Removal

Delete a VM and simultaneously wipe its virtual storage volume.

```bash
virsh undefine <vm-name> --remove-all-storage
```

- Note: May need to add additional flags `--nvram --snapshots-metadata`.

### Purge a VM and Remove a Specific Storage Volume

Delete a VM and a specified storage volume.

```bash
virsh undefine <vm-name> --storage <target>
```

- Note: Replace <target> with storage identifier found via `virsh domblklist` (e.g., `vda`), see next command.

### Fetch Virtual Disk Layout

Retrieve the exact block device target and storage backing path for VM, (usually `vda` or `hda`). Useful before executing cleanups.

```bash
virsh domblklist <vm-name>
```

### Enable Autostart

Configures the virtual machine to automatically boot whenever the host system starts up.

```bash
virsh autostart <vm-name>
```

### Disable Autostart

Prevents the virtual machine from starting automatically during host boot.

```bash
virsh autostart --disable <vm-name>
```

---

### Environment & Storage Defaults

- **Default Disk Image Directory**: `/var/lib/libvirt/images`
- **Configuration XML Directory**: `/etc/libvirt/qemu/`

---
