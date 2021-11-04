# Openshift 4 Backup Automation

This tool was built to automate the steps to create an Openshift 4 backup described on https://docs.openshift.com/container-platform/4.7/backup_and_restore/control_plane_backup_and_restore/backing-up-etcd.html

Cronjob **openshift-backup** resource  will be created and scheduled to run at 11:56 PM (GMT) and keep last 3 days on backup's directory. All files with more than 3 days will be removed from the backups directory.

### Apply yaml to create Openshift resources

`oc apply -f openshift4-backup.yaml`

### Privileged permissions

Grant access to the **privileged** scc to the service account **openshift-backup** running the Cronjob.

`oc adm policy add-scc-to-user privileged -z openshift-backup -n ocp-backup-etcd`

