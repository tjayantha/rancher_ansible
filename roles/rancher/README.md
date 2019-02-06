Rancher Work flow:

Default configuration parameters are defined in the "./defaults/main.yml" which is self explanatory. 

The tasks/rancher_server.yml execute below configuration and ensure Rancher Master Server is Up and running, Which internally calls the restapi.
    - name: Container is already running.
    - name: Start rancher server
    - name: Check Rancher Server "{{ rancher_server_url }}" accessible from UI
    - name: Authenticate & retrieve APIKEY
    - name: Retrieve secert Key
    - name: Authenticate & Reset the Default Admin password
    - name:  Set Rancher Server URL "{{ rancher_server_url }}"
    - name: Enable Helm in catalog
    - name: Test and Apply Active Directory Configuration
    - name: Creates cacerts directory
    - name: Get CaCerts
    - name: Create cacerts file

Base Modules: Which is a generic playbooks uses the Rancher RestAPI 
    - rancher_cluster.yml
    - join_etcd_cplane.yml
    - join_worker_node.yml
    - add_catalogs.yml

Example: 
    sandbox.cluster.yml  creates "sandbox" cluster in the rancher_server, which includes above base modules and define the default variables. Create new YML for corresponding clusters.

main.yml palybook includes rancher_server.yml and <cluster-name>.cluster.yml
