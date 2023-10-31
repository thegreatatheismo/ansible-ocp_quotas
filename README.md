# Kustomize Overlay for OpenShift Namespace Quotas

This repository contains a Kustomize overlay for managing resource quotas in an OpenShift namespace.

## Usage

1. Clone this repository to your local machine:

```bash
git clone https://github.com/your_username/your_repository.git
```

2. Edit the `create_kustomize_overlay.yml` playbook to customize the namespace and quota limits.

3. Run the playbook to generate the Kustomize overlay:

```bash
ansible-playbook configure.yml
```

4. Apply the overlay to your OpenShift cluster using Kustomize:

```bash
kustomize build ./kustomize/{{ kustomize_vars.namespace }}/ | kubectl apply -f -
```

## Variables

- `_ansible_dir`: The directory in which the existing quota files live
- `name.funding_source`: The funding source of the quota
- `name.project`: The name of the organisational project (not to be confused with the OCP namespace/project)
- `name.namespace`: The namespaces to be added to the quota (as a list)
- `requests.pods`: The number of pods requested
- `requests.cpu`: The number of CPUs requested
- `requests.memory`: The amount of memory requested (in Mi/Gi)
- `requests.storage`" The amount of storage requested (in Mi/Gi/Ti)
- `limits.cpu`: The limit for CPU
- `limits.memory`: The limit for Memory (in Mi/Gi)
- `lrange.pod.max_cpu`: The maximum CPU per pod
- `lrange.pod.max_memory`: The maximum Memory per pod (in Mi/Gi)
- `lrange.pod.min_cpu`: The minimum CPU per pod
- `lrange.pod.max_memory`: The minimum memory per pod (in Mi/Gi)
- `lrange.container.default_cpu`: The default CPU per container
- `lrange.container.defaultmemory`: The default memory per container (in Mi/Gi) 
- `lrange.container.defaultRequest_cpu`: The default request for container CPU
- `lrange.container.defaultRequest_memory`: The default request for container memory (in Mi/Gi)

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
