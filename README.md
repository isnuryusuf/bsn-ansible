
This is a collection of Ansible modules for Big Switch products.  There are two modules so far: one to gather *facts* for Big Cloud Fabric and another to gather *facts* for Big Monitoring Fabric.

This is extremely easy to test using Big Switch's online labs: http://labs.bigswitch.com/home.  All you need to do is clone this repository and update the IP address found in the [hosts](hosts) file with the IP of your controller (for BCF, BMF, or both)

The facts gathered can be used as inputs to other modules or used in templates to create documentation used for inventorying, assessments, etc.

* The facts returned for Big Cloud Fabric are returned as a dictionary using the key `bsnbcf`.
* The facts returned for Big Monitoring Fabric are returned as a dictionary using the key `bsnbmf`.
* Creating tenant.
* Creating Segment.


[Example Playbook](bsn.yml):

```yaml
---

   - name: GATHER FACTS FROM BIG SWITCH CONTROLLERS
     hosts: bcf
     connection: local

     tasks:

       - name: GATHER FACTS
         bcf_get_facts: controller={{ controller_ip }} username={{ un }} password={{ pwd }}

       - name: DUMP FACTS TO TERMINAL
         debug: var=bsnbcf


```

Executing Playbook:

```
$ ansible-playbook -i hosts bsn.yml 
```


Creating Tenant:

```
$ ansible-playbook -i hosts tenant.yml 
```

Creating Segment:

```
$ ansible-playbook -i hosts segment.yml 
```

Creating Tenant & Segment:

```
$ ansible-playbook -i hosts tenant-segment.yml 
```
