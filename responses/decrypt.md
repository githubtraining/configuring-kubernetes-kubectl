## Deploying a Container App To A Kubernetes Cluster

There are many ways to deploy applications to Kubernetes. The HELM utility is an excellent way to simplify the process and manage many dependencies. Our focus here is on the minimal workflow necessary and we wish to simplify the process. This means we will use the Kubernetes command line utility called 'kubectl' for our purposes.

#### Configuraing kubectl

On any client platform 'kubectl' must be configured to make calls to the Kubernetes API Server. Dependent upon how you install Kubernetes, there are various ways that the Kubernetes Configuration file is handled. It can usually be found in the /etc/kubernetes directory on the Kubernetes Master server instance.

In our example we have placed an encrypted Kubernetes Configuration file in our repository and it is in the secrets folder and named k8s_config.gpg. In a prior workflow step we have decrypted the Kubernetes Configuration file using the gpg utility with a secret passphrase stored in the vault.

The new decrypted file has been placed in the present working directory and has been named by its basename k8s_config without the gpg extension.

The example for this decryption is below:

<table>
<tr><td>
<img width="1111" alt="Screen Shot 2019-09-23 at 3 43 58 PM" src="https://user-images.githubusercontent.com/43185011/65457213-0f139100-de19-11e9-954e-3d642212f552.png">
</tr></td>
</table>
