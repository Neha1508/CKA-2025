# CKA-2025
CKA 2025 full exam guide

## CKA Exam Detials
Mode of exam: Online
Duration of Exam 2 hours
Certification Valid for 2 Years
Includes 12 Month Exam Eligibility
One Retake
PDF Certificate and Digital Badge
Software Version: **Kubernetes v1.33**
Performance-Based Exam
Exam Simulator
Number of questions: 16
**------------------------------------------------------------------------------------------------------------------------------------------------**
## CKA 2025 Questions ##

**QUESTION:1**
**Install Argo CD using Helm (without CRDs)**

Install Argo CD in a Kubernetes cluster using Helm, while ensuring that CRDs are NOT installed (they are already pre-installed).

Follow the steps below:

Requirements:

Add the official Argo CD Helm repository with the name argo.

Generate a Helm template from the Argo CD chart version 7.7.3 for the argocd namespace.

Ensure that CRDs are not installed by configuring the chart accordingly.

Save the generated YAML manifest to:

/home/argo/argo-helm.yaml

**QUESTION:2**
**Sidecar Container**

Update the existing Deployment wordpress by adding a sidecar container named sidecar using the image busybox:stable to the existing Pod.

Requirements:

The new sidecar container must run the following command:

/bin/sh -c "tail -f /var/log/wordpress.log"
Use a shared volume mounted at /var/log so that the log file wordpress.log is available to the co-located container.

**QUESTION:3**
**Ingress to Gateway API Migration**

You have an existing web application deployed in a Kubernetes cluster using an Ingress resource named web.

You must migrate the existing Ingress configuration to the new Kubernetes Gateway API, while maintaining the existing HTTPS access configuration.

Tasks:

Create a Gateway resource named web-gateway with the hostname gateway.web.k8s.local that:

Maintains the existing TLS configuration

Maintains the existing listener configuration from the current Ingress resource named web

Create an HTTPRoute resource named web-route with the hostname gateway.web.k8s.local that:

Maintains the existing routing rules from the current Ingress resource named web

Note:

A GatewayClass named nginx-class is already installed in the cluster.

**QUESTION: 4**
**Pod Resource Requests & Limits**

You are managing a WordPress application running in a Kubernetes cluster.

Your task is to adjust the Pod resource requests and limits to ensure stable operation. Follow the instructions below:

Tasks:

Scale down the wordpress Deployment to 0 replicas.

Edit the Deployment and divide node resources evenly across all 3 Pods.

Assign equal CPU and memory requests to each Pod.

Add sufficient overhead to avoid node instability.

Ensure that both the init containers and main containers use exactly the same resource requests and limits.

After making the changes, scale the Deployment back to 3 replicas.

**QUESTION:5**
**StorageClass**

Create a new StorageClass named local-kiddle with the provisioner rancher.io/local-path.

Requirements:

Set volumeBindingMode to WaitForFirstConsumer.

Configure the StorageClass as the default StorageClass.

Do not modify any existing Deployments or PersistentVolumeClaims.

**QUESTION:06**
**Priority Class**

You’re working in a Kubernetes cluster with an existing Deployment named busybox-logger running in a namespace called priority.

The cluster already has at least one user-defined PriorityClass.

Tasks:

Create a new PriorityClass named high-priority for user workloads.

The value of this PriorityClass must be exactly one less than the highest existing user-defined PriorityClass value.

Patch the existing Deployment busybox-logger in the priority namespace to use the newly created high-priority PriorityClass.

**QUESTION:7**
**Ingress Resource**

Create a new Ingress resource named echo in the echo-sound namespace.

Tasks:

Expose the deployment using a Service named echo-service on path http://example.org/echo, using:

Service port: 8080

Service type: NodePort

Verify the availability of the echo-service using the following command, which should return 200:

curl -o /dev/null -s -w "%{http_code}\n" http://example.org/echo

**QUESTION:8**
**CRDs**
Task:

Create a list of all cert-manager CRDs and save it to ~/resources.yaml.

Make sure kubectl uses the default output format when listing the CRDs.

Using kubectl, extract the documentation for the subject specification field of the Certificate Custom Resource and save it to ~/subject.txt.

You may use any output format that kubectl supports.


**QUESTION:09**
**NetworkPolicy**

There are two deployments, Frontend and Backend.

Frontend is deployed in the frontend namespace.

Backend is deployed in the backend namespace.

Task:

Create a NetworkPolicy that allows interaction between the frontend and backend deployments.

The NetworkPolicy must be least permissive.

**QUESTION: #10**
**HPA**

Create a new HorizontalPodAutoscaler (HPA) named apache-server in the autoscale namespace.

Tasks:

Configure the HPA to target the existing deployment named apache-deployment in the autoscale namespace.

Set the HPA target to 50% CPU usage per pod.

Configure the HPA with:

Minimum replicas: 1

Maximum replicas: 4

Downscale stabilization window: 30 seconds

**QUESTION:11** 
**Container Network Interface (CNI)**

Install and configure a CNI of your choice that meets the specified requirements.
Choose one of the following options:

Flannel (v0.26.1) using the manifest:
kube-flannel.yml
(https://github.com/flannel-io/flannel/releases/download/v0.26.1/kube-flannel.yml
)

Calico (v3.28.2) using the manifest:
tigera-operator.yaml
(https://raw.githubusercontent.com/projectcalico/calico/v3.28.2/manifests/tigera-operator.yaml
)

The CNI you choose must:

Allow pods to communicate with each other

Support network policy enforcement

Be installed from manifest

**QUESTION:12**
**PVC**

A Persistent Volume already exists and is retained for reuse.

Create a PersistentVolumeClaim named MariaDB in the mariadb namespace with the following requirements:

Access mode: ReadWriteOnce

Storage capacity: 250Mi

Edit the maria-deployment defined in the file located at maria_deploy.yaml to use the newly created PVC.

Finally, verify that the deployment is running and stable.

**QUESTION:13**
**CRI-Dockerd**
Task:

Set up cri-dockerd.

Steps:

Install the Debian package

./cri-dockerd_0.3.9-0.ubuntu-jammy_amd64.deb


using dpkg.

Enable and start the cri-dockerd service.

Configure the following system parameters:

Set net.bridge.bridge-nf-call-iptables to 1

Set net.ipv6.conf.all.forwarding to 1

Set net.ipv4.ip_forward to 1

Set net.netfilter.nf_conntrack_max to 131072

**QUESTION:14**
**Troubleshooting**

After a cluster migration, the control plane kube-apiserver is not coming up.

Before migration:

etcd was external and running in HA mode.

After migration:

kube-apiserver is pointing to the etcd peer port 2380 instead of 2379.

Task:

Fix the issue so that the kube-apiserver can start correctly.


**QUESTION:15**
**Taints & Tolerations**
Task:

Add a taint to node01 so that no normal pods can be scheduled on the node.

Use the following taint:

Key = TI

Value = Value

Effect = NoSchedule

Schedule a Pod on node01 by adding the correct toleration to the pod specification and ensure that it lands on the correct node.


**QUESTION:16**
**NodePort**

There is a deployment named nodeport-deployment in the relevant namespace.

Tasks:

Configure the deployment so it can be exposed using port 80 and protocol TCP, with the port name http.

Create a new Service named nodeport-service exposing the container on port 80 using TCP.

Configure the new Service to also expose the individual pods using NodePort.

**QUESTION:17**
**TLS**

There is an existing deployment called nginx-static in the nginx-static namespace.
The deployment contains a ConfigMap that supports TLSv1.2 and TLSv1.3, and a Secret for TLS.

There is a service called nginx-static in the nginx-static namespace that is currently exposing the deployment.

Tasks:

Configure the ConfigMap to only support TLSv1.3.

Add the IP address of the service in /etc/hosts and name it ITKdidde.k8s.local.

Verify that everything is working using the following commands:

curl --tls-max 1.2 https://ITKdidde.k8s.local -k    # (TLSv1.2 should not work)
curl --tlsv1.3 https://ITKdidde.k8s.local -k
Sol.

**-----------------------------------------------------------------------**


