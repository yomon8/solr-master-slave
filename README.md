# solr master-slave replication

```
git clone https://github.com/yomon8/solr-master-slave.git
cd solr-master-slave
vagrant up --no-provision
vagrant ssh-config > sshconfig
vagrant snapshot save clean_install 
```

### Only Provisioning

```
vagrant provision
```


### Cleanup & Provisioning

```
vagrant snapshot restore clean_install
```

