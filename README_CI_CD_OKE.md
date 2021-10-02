## Overview

This a general guideline to setup a **CI/CD using OCI DevOps** to deploy app on a Kubernetes cluster (**OKE**).

### 1. Gather Required Info
```
OCI Username: <oci-username>	# eg: oracleidentitycloudservice/user01_idcs
OCI Auth Token: <oci-auth-token>	
Tenancy Name: <tenancy-name>	
Tenancy Namespace: <tenancy-namespace>	# object storage namespace, eg: ansh81vru1zp

Region Key: <region-key>	# eg: iad

OCIR Docker Username: 
<tenancy-namespace>/<oci-username>#eg-ansh81vru1zp/oracleidentitycloudservice/user01

OCIR Docker Password: <oci-auth-token>

OCIR Repo Name: # <ocir-repo-name> # eg: project01/mywebapp
OCIR Repo Compartment: <ocir-comp-name>	# :ASEAN/Jahangir/Demo
OCIR Region: <ocir-region> # eg: Singapore

OCI Code Repo (git) Username: <tenancy-name>/<oci-username> 
OCI Code Repo (git) Password: <oci-auth-token>

Vault Secret OCID (oci-auth-token): <vault-secret-ocid>
```

### 2. Spin up a Kubernetes cluster
```
a. create secret docker registry
$ kubectl create secret docker-registry <secret-name> --docker-server=<region-key>.ocir.io --docker-username='<tenancy-namespace>/<oci-username>' --docker-password='<oci-auth-token>' --docker-email='<email-address>'


b. create any other resource (eg: namespace, secret, pv etc) fullfill app requirements (if any) 
```

### 3. Create OCIR Repository, take notes at section1

### 4. Create Vault, MEK, Secret and note OCID of secret at section1

### 5. Setup OCI DevOps (CI/CD)
##### a) Create DevOps Project
```
i. Create notification topic
ii. Create DevOps project
iii. Enable logging
```
##### b) Create A Code Repository
```
i. Clone the empty repo to client machine
ii. Copy application codes
iii. Push to OCI Code Repo
```
##### c) Create DevOps environment selecting OKE Cluster

##### d) Edit the build_spec.yaml file

##### e) edit the deploy-web.yaml file

##### f) Create Build Pipeline

##### g) Create Deployment Pipeline