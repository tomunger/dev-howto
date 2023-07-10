

## Startup and Shutdown

    microk8s start
    microk8s stop

## VSCode

Create configuration for microk8s

    microk8s.kubectl config view --raw > $HOME/.kube/config

    

## Status

    microk8s status --wait-ready

    microk8s.kubectl config view