Rancher Work flow:
 <br />
    Default configuration parameters are defined in the "./defaults/main.yml" which is self explanatory. 
 <br />
 <br />The tasks/rancher_server.yml execute below configuration and ensure Rancher Master Server is Up and running, Which internally calls the restapi.
   <br />  - name: Container is already running.
   <br />  - name: Start rancher server
   <br />  - name: Check Rancher Server "{{ rancher_server_url }}" accessible from UI
    <br /> - name: Authenticate & retrieve APIKEY
    <br /> - name: Retrieve secert Key
    <br /> - name: Authenticate & Reset the Default Admin password
    <br /> - name:  Set Rancher Server URL "{{ rancher_server_url }}"
    <br /> - name: Enable Helm in catalog
   <br />  - name: Test and Apply Active Directory Configuration
   <br />  - name: Creates cacerts directory
   <br />  - name: Get CaCerts
   <br />  - name: Create cacerts file

 <br />Base Modules: Which is a generic playbooks uses the Rancher RestAPI 
    <br /> - rancher_cluster.yml
   <br />  - join_etcd_cplane.yml
   <br />  - join_worker_node.yml
   <br />  - add_catalogs.yml

 <br />Example: 
   <br />  sandbox.cluster.yml  creates "sandbox" cluster in the rancher_server, which includes above base modules and define the default variables. Create new YML for corresponding clusters.

 <br />main.yml palybook includes rancher_server.yml and <cluster-name>.cluster.yml
