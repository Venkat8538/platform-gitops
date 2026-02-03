# platform-gitops

GitOps source-of-truth for Kubernetes deployments managed by Argo CD.

## Structure
- `apps/` contains Argo CD Application manifests
- `envs/` contains per-environment Helm values overrides

## Workflow
- App repo builds/pushes image to ECR
- CI updates `envs/<env>/<app>-values.yaml` with the new image tag
- Argo CD detects the Git change and syncs the cluster
