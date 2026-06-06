# Kubernetes on Windows with Minikube and Docker

This guide shows how to install and run a local Kubernetes cluster on Windows using Minikube and Docker.

## Prerequisites

- Windows 10/11 or Windows Server with WSL2 support
- Docker Desktop installed and running, or Docker Engine configured for Windows
- PowerShell opened as Administrator
- `choco` (Chocolatey) package manager installed

## Install Chocolatey (if needed)

If Chocolatey is not installed yet, run this command in an elevated PowerShell window:

```powershell
Set-ExecutionPolicy Bypass -Scope Process -Force
[System.Net.ServicePointManager]::SecurityProtocol = [System.Net.ServicePointManager]::SecurityProtocol -bor 3072
iex ((New-Object System.Net.WebClient).DownloadString('https://community.chocolatey.org/install.ps1'))
```

## Install Kubernetes CLI and Minikube

```powershell
choco install kubernetes-cli -y
choco install minikube -y
```

## Verify the installations

```powershell
kubectl version --client
minikube version
```

## Start Minikube with Docker

Use Docker as the driver and start the local cluster:

```powershell
minikube start --driver=docker
```

## Verify the cluster

```powershell
kubectl cluster-info
kubectl get nodes
```

## Useful commands

- `minikube status` — check Minikube status
- `minikube dashboard` — open the Kubernetes dashboard in a browser
- `minikube stop` — stop the Minikube cluster
- `minikube delete` — remove the local cluster

## Notes

- Ensure Docker Desktop is running before starting Minikube.
- If Docker is not available, you can use another supported Minikube driver such as `hyperv` or `virtualbox`.
