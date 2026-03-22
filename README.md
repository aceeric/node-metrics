# Node Metrics

A simple node metrics collector in Python.

## Install

kubectl -n node-metrics apply -f\
namespace.yaml,\
configmap.yaml,\
serviceaccount.yaml,\
clusterrole.yaml,\
clusterrolebinding.yaml,\
deployment.yaml,\
service.yaml,\
servicemonitor.yaml

## Logs

POD=$(kubectl -n node-metrics get po -l app=node-metrics -oname)
kubectl -n node-metrics log -f $POD

## Cleanup

kubectl delete clusterrole node-metrics-reader
kubectl delete clusterrolebinding node-metrics-reader-binding
kubectl delete namespace node-metrics

## Alternate kubernetes client install

```
git clone --recursive https://github.com/kubernetes-client/python.git
cd python
python -m pip install --upgrade .
```

