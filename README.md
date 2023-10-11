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
ansible-playbook create_kustomize_overlay.yml
```

4. Apply the overlay to your OpenShift cluster using Kustomize:

```bash
kustomize build ./kustomize/{{ kustomize_vars.namespace }}/ | kubectl apply -f -
```

## Variables

- `namespace`: The name of the OpenShift namespace where the quota will be applied.
- `cpu_limit`: The CPU resource limit for the namespace.
- `memory_limit`: The memory resource limit for the namespace.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.
