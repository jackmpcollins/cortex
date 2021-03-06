# Environments

When you create a cluster with `cortex cluster up`, an environment with the same name as your cluster is automatically created to point to your cluster and is configured to be the default environment. You can name the environment something else via the `--configure-env` flag, e.g. `cortex cluster up --configure-env prod`. You can also use the `--configure-env` flag with `cortex cluster info` to create / update the specified environment.

You can list your environments with `cortex env list`, change the default environment with `cortex env default`, rename an environment with `cortex env rename`, delete an environment with `cortex env delete`, and create/update an environment with `cortex env configure`.

## Multiple clusters

```bash
cortex cluster up cluster1.yaml --configure-env cluster1  # configures the cluster1 env
cortex cluster up cluster2.yaml --configure-env cluster2  # configures the cluster2 env

cortex deploy --env cluster1
cortex delete my-api --env cluster1

cortex deploy --env cluster2
cortex delete my-api --env cluster2
```

## Multiple clusters, if you omitted the `--configure-env` on `cortex cluster up`

```bash
cortex cluster info cluster1.yaml --configure-env cluster1  # configures the cluster1 env
cortex cluster info cluster2.yaml --configure-env cluster2  # configures the cluster2 env

cortex deploy --env cluster1
cortex delete my-api --env cluster1

cortex deploy --env cluster2
cortex delete my-api --env cluster2
```

## Configure `cortex` CLI to connect to an existing cluster

If you are installing the `cortex` CLI on a new machine, you can configure it to access an existing Cortex cluster.

On the machine which already has the CLI configured, run:

```bash
cortex env list
```

Take note of the environment name and operator endpoint of the desired environment.

On your new machine, run:

```bash
cortex env configure
```
