# Entrega 3: Canary release con Istio

App Flask + Redis (práctica 07) con una v1 y una v2 detrás del mismo Service y el mismo Redis,
expuestas por el ingress gateway de Istio con un reparto 90% v1 / 10% v2.

- `app-v2/`: código de la v2 (guarda el JSON completo, cabecera `X-App-Version: v2`, endpoint `/version`)
- `k8s/`: Redis, Deployments `asr-flask-v1` y `asr-flask-v2` (label `version`) y el Service compartido `asr-flask`
- `istio/`: Gateway, DestinationRule (subsets v1/v2), VirtualService inicial y VirtualService canary 90/10,
  y los valores de Helm del ingress gateway (IPs permitidas)
