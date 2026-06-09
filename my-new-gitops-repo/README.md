# my-new-gitops-repo

GitOps-Repository für Argo CD mit App-of-Apps-Muster.

## Struktur

```
base-repo (Root-Application)
├── nginx          → Application (deployed Pods in Namespace nginx)
├── podinfo        → Application (deployed Pods in Namespace podinfo)
├── team-a         → Application (Team-Repo my-team-repo)
└── my-first-webserver → AppProject
```

## Bootstrap

Einmalig anwenden, damit Argo CD die Kind-Applications verwaltet:

```bash
kubectl apply -f base-repo.yaml
```

Danach synchronisiert `base-repo` automatisch `nginx.yaml`, `podinfo.yaml`, `team-a.yaml` und `project.yaml` aus dem Repo-Root.
