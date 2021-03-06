# End to End Tests

We use [Kind](https://github.com/kubernetes-sigs/kind) to run our tests.

To get everything setup run:

```
kind_test_setup.sh
```

Activate kind kubernetes config:

```
export KUBECONFIG="$(kind get kubeconfig-path)"
```

Then to run the tests and log output to a file:

```
make test > test.log
```

To also follow controller logs in a separate terminal:
```
export KUBECONFIG="$(kind get kubeconfig-path)"
kubectl logs -f -n seldon-system $(kubectl get pods -n seldon-system -l app=seldon -o jsonpath='{.items[0].metadata.name}')
```