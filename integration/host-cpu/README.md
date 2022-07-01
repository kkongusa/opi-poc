# Host Main BMC

Runs nvme-cli and fio and some DB, example:

<!-- markdownlint-disable -->
```text
$ nvme list
Node                  SN                   Model                                    Namespace Usage                      Format           FW Rev
--------------------- -------------------- ---------------------------------------- --------- -------------------------- ---------------- --------
/dev/nvme0n1          71T0A0CETC88         Dell Ent NVMe CM6 MU 1.6TB               1          14.79  GB /   1.60  TB    512   B +  0 B   2.1.3
/dev/nvme1n1          71T0A0BGTC88         Dell Ent NVMe CM6 MU 1.6TB               1         888.31  MB /   1.60  TB    512   B +  0 B   2.1.3
/dev/nvme2n1          71T0A0C3TC88         Dell Ent NVMe CM6 MU 1.6TB               1         524.29  kB /   1.60  TB    512   B +  0 B   2.1.3
/dev/nvme3n1          71T0A0C9TC88         Dell Ent NVMe CM6 MU 1.6TB               1         524.29  kB /   1.60  TB    512   B +  0 B   2.1.3
```
<!-- markdownlint-restore -->

fio example:
<!-- markdownlint-disable -->
```text
sudo fio --direct=1 --prio=0 --norandommap=1 --group_reporting --cpus_allowed_policy=split --ioengine=libaio --rw=randrw --rwmixread=100 --bs=4096 --runtime=100 --numjobs=16 --iodepth=4 --name=filename1 --filename=/dev/nvme0n1 --name=filename2 --filename=/dev/nvme0n2 --name=filename3 --filename=/dev/nvme0n3
```
<!-- markdownlint-restore -->