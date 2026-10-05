# Armanstar Pharmacy infrastructure

Run from `/root/apps/armanstar-pharmacy` on the VPS.

## Generate environment

```sh
sh scripts/generate-env.sh
```

Creates `envs/env.prod` from `k8s/env.example`. Existing values are preserved;
only missing variables are added. Fill in the values and set `PORT=3001` before deploying.

## Apply updates

```sh
sh scripts/apply-update.sh
```

Creates the `armanstar` namespace if needed, loads `envs/env.prod` into the
`armanstar-pharmacy-env` Secret, and applies the deployment, service, and ingress.
Unchanged ingress stays unchanged. Restarts the app's pods and waits up to
120 seconds for the rollout.
