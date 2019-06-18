# Demo via Porter

In this demo we are going to take the [RabbitMQ Golang](https://github.com/kedacore/sample-go-rabbitmq) and make some modifications so the consumer only scales on [virtual node](https://cda.ms/XL).  
This is accomplished by seeting up or cluster with virtual node enabled and adding the following to the [consumer.yaml](manifests/consumer/consumer.yaml)
```
dnsPolicy: ClusterFirst
      nodeSelector:
        kubernetes.io/role: agent
        beta.kubernetes.io/os: linux
        type: virtual-kubelet
      tolerations:
      - key: virtual-kubelet.io/provider
        operator: Exists
      - key: azure.com/aci
        effect: NoSchedule
```            
## Prerequisites

Good news there are none as well have already installed them all.

# Build

Make sure you are back in the root of the demo directory where the porter.yaml file lives and issue 

```
porter build
```

# Creating credentials
We are going to reuse the credentials file that we created in the previous bundle as it only contains our `kuneconfig` info  

# Install
Now we can install the bundle referencing the credential we created in the previous step with `-c keda` flag. The `-c` is for credentials and the name `keda` come from the name of the previous bundle.

```
porter install -c keda
```
No we want to prove the scaling is happening by watching the horizontal pod autoscaler in another terminal run

```
kubectl get hpa -w
```
And then watch the pods and make sure that they are only scaling on virtual node in another terminal run

```
kubectl get pods -o wide
```

# Clean up 

To stop the pods scaling we will use the uninstall command that porter ships with and pass the credentials to talk to our cluster.
```
porter uninstall -c keda
```

To check the scaling has stopped you can use the commands from above

```
kubectl get hpa -w
```
and also there are no pods left with 
```
kubectl get pods -o wide
```