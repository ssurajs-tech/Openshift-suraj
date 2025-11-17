# OpenShift Concepts — Quick Reference

This repository contains an overview of containers, Kubernetes, and Red Hat OpenShift Container Platform (RHOCP) concepts. The content below collects the most important ideas and common commands you will use when working with OpenShift clusters.

## Table of contents

- [About this repo](#about-this-repo)
- [Containers & containerization](#containers--containerization)
- [Kubernetes primitives and OpenShift](#kubernetes-primitives-and-openshift)
- [Images & registries](#images--registries)
- [Workloads & deployment strategies](#workloads--deployment-strategies)
- [Networking: Services & Routes](#networking-services--routes)
- [Configuration: ConfigMaps & Secrets](#configuration-configmaps--secrets)
- [Storage: PVs, PVCs, StorageClass](#storage-pvs-pvcs-storageclass)
- [Stateful workloads](#stateful-workloads)
- [High availability & scaling](#high-availability--scaling)
- [Common commands & tools](#common-commands--tools)
- [Best practices](#best-practices)
- [Further reading](#further-reading)

## About this repo

Use this document as a compact guide to the core concepts you’ll encounter when deploying and operating containerized applications on Kubernetes and OpenShift.

## Containers & containerization

- A container packages an application process with its runtime dependencies so it can run consistently across environments.
- Containerization improves portability and modularity, making development and maintenance of application components easier.
- Containers are designed to be immutable and ephemeral — prefer rebuilding images and redeploying instead of mutating running containers.

## Kubernetes primitives and OpenShift

- A Pod is the smallest deployable unit in Kubernetes and may contain one or more containers that share networking and storage.
- OpenShift builds on Kubernetes and provides additional enterprise features, a web console for administration, integrated CI/CD tooling, image streams, and security enhancements.

## Images & registries

- Container images produce runnable instances. Images are stored and distributed via registries (Quay.io, Red Hat Container Catalog, Docker Hub, etc.).
- You can reference images by tags or by immutable digests (SHA) — using digests guarantees you get the exact image you expect.
- Tools: `oc image` (OpenShift) and `skopeo` for inspecting and copying images.

## Workloads & deployment strategies

- Deployments are a common way to run stateless applications. They manage ReplicaSets and support rollout strategies such as rolling updates and recreate.
- Jobs run one-off or batch tasks; the cluster will retry according to job spec until success or a configured backoff limit.
- The workload API offers different resources depending on lifecycle and scheduling needs (Deployment, Job, CronJob, DaemonSet, StatefulSet).

## Networking: Services & Routes

- Services provide stable network endpoints for pods inside the cluster.
- Routes (OpenShift) expose services externally by mapping a public hostname to an internal service IP.

## Configuration: ConfigMaps & Secrets

- ConfigMaps inject non-sensitive configuration data into pods.
- Secrets store sensitive data (values are base64-encoded) — treat them carefully and use proper RBAC and encryption-at-rest if available.

## Storage: PVs, PVCs, StorageClass

- A PersistentVolume (PV) is cluster storage. A PersistentVolumeClaim (PVC) is a request for storage by a pod.
- StorageClass enables dynamic provisioning of PVs and describes different storage types (performance, reclaimPolicy, volume mode: Block vs Filesystem).

## Stateful workloads

- StatefulSet manages pods that require stable, unique network IDs and stable storage (each pod gets its own PV).

## High availability & scaling

- Build HA into applications using probes (liveness/readiness), resource requests/limits, and multiple replicas.
- Horizontal Pod Autoscalers (HPA) scale replicas based on resource usage or custom metrics.

## Common commands & tools

- oc new-app — create resources from source image heuristics
- oc apply/get/describe/rollout — manage resources and check status
- oc image — inspect image streams and images
- skopeo — inspect and copy images between registries

## Best practices

- Keep containers immutable: rebuild images for changes.
- Use image digests for reproducible deployments when appropriate.
- Set resource requests and limits to avoid noisy-neighbor issues.
- Configure readiness and liveness probes to let the cluster manage traffic routing correctly.
- Use ConfigMaps and Secrets for configuration and sensitive values respectively; enable encryption-at-rest for secrets when supported.

## Further reading

- Kubernetes documentation: https://kubernetes.io/docs/
- OpenShift documentation: https://docs.openshift.com/
- Red Hat Container Catalog: https://catalog.redhat.com/

---

If you want, I can:

- Add examples with `oc` commands and YAML manifests.
- Create a short quickstart that deploys a sample app to OpenShift.
- Add links to learning resources and diagrams.

Tell me which of these you'd like next.


   