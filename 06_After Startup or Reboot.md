### Restart Gangila
```
pdsh -w c[1-2] systemctl restart gmond
pdsh -w c[1-2] systemctl restart gmetad
systemctl restart gmond
systemctl restart gmetad
```

### Restart Slurm
```
pdsh -w c[1-2] systemctl restart slurmd
systemctl restart slurmd
systemctl restart slurmdbd
systemctl restart slurmctld
```

### Check Slurm status
```
scontrol show node
sinfo
```

### How to “undrain” slurm nodes in drain state

**Example:**
Using sinfo it shows 3 nodes are in drain state,

PARTITION AVAIL  TIMELIMIT  NODES  STATE NODELIST\
all*         up   infinite      3  drain node[10,11,12]

```
scontrol: update NodeName=node10 State=DOWN Reason="undraining"
scontrol: update NodeName=node10 State=RESUME
scontrol: show node node10
```

**If no jobs are currently running on the node:**
```
scontrol update nodename=node10 state=idle
```

**If jobs are running on the node:**
```
scontrol update nodename=node10 state=resume
```

