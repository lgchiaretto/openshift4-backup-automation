# Openshift 4 Backup Automation

This tool was built to automate the steps to create an Openshift 4 backup described on https://docs.openshift.com/container-platform/4.8/backup_and_restore/backing-up-etcd.html#backup-etcd

Cronjob **openshift-backup** resource  will be created and scheduled to run at 11:56 PM and keep last 3 days on backup's directory. All files with more than 3 days will be removed from the backups directory.

### Prerequesites

Create a new project called ocp-backup-etcd

`oc new-project ocp-backup-etcd --description "Openshift Backup Automation Tool"` 

### Apply yaml to create Openshift resources

`oc apply -f openshift4-backup.yaml`

### Privileged permissions

Grant access to the **privileged** scc to the service account **openshift-backup** running the Cronjob.

`oc adm policy add-scc-to-user privileged -z openshift-backup`

