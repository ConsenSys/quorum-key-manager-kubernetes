# Quorum Key Manager Kubernetes

This repository contains an implementation example on how to deploy the Quorum Key Manager with Hashicorp Vault using Kubernetes and Helm charts.

# 1. Installing Quorum Key Manager

## 1.1. Quickstart

1. To deploy a simple Quorum Key Manager (not production ready) and with Hashicorp Vault, run the following command:

```bash
helmfile apply --suppress-secrets
```

2. Once deployed you could easily test the Quorum Key Manager API in http://localhost:8080:

```
kubectl port-forward --namespace qa-qkm svc/quorum-key-manager-quorumkeymanager 8080:8080
```

[See Quorum Key Manager APIs documentation](https://consensys.github.io/quorum-key-manager)

## 1.2. Delete Quorum Key Manager
!!!hint
  to delete Quorum Key Manager's deployment and its ressources run the following commands:

```bash
helmfile delete --purge
kubectl delete namespace qa-qkm
```
# 2. Hashicorp Vault

## 2.1 Enable auditing

Once vault auditing has been enabled, you will need to activate it by running the following command

```bash
kubectl exec -ti $POD NAME --  vault audit enable file file_path=/vault/audit/vault_audit.log
```