# Keda via Porter

## Prerequisites
For the environment to build you will need the following software installed
 - [Porter](https://porter.sh/)
 - [Docker](https://www.docker.com/)

Install Porter, Docker and Golang as per the instructions above 

Now we are ready to build the bundle

# Build

Make sure you are back in the root of the keda directory where the porter.yaml file lives and issue 

```
porter build
```

# Creating credentials
This CNAB bundle needs to have access to your `$HOME/.kube/config` file to talk to your Kubernetes cluster. Porter will create the credential file we will use. To create this file we issue the following command  
```
porter credentials generate
```

You will get a text menu like below
```
Generating new credential keda from bundle keda
==> 1 credentials required for bundle keda
? How would you like to set credential "kubeconfig"  [Use arrows to move, space to select, type to filter]
  specific value
> environment variable
  file path
  shell command
```

Chose file path option and add the following value
```
? Enter the path that will be used to set credential "kubeconfig" $HOME/.kube/config
```

# Install
Now we can install the bundle referencing the credential we created in the previous step with `-c keda` flag. The `-c` is for credentials and the name `keda` come from the name of this bundle.

```
porter install -c keda
```

Now we are reading to deply our [demo application](../demo/README.md)
