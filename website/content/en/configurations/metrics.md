---
type: docs
title: "Metrics provided by Azure Keyvault Provider for Secrets Store CSI Driver"
linkTitle: "Metrics"
weight: 1
---

The Azure Keyvault Provider for Secrets Store CSI Driver uses [opentelemetry](https://opentelemetry.io/) for reporting metrics. This project is under [active development](https://github.com/open-telemetry/opentelemetry-go#release-schedule).

Prometheus is the only exporter that’s currently supported with the driver.

### List of metrics provided by the Azure Keyvault Provider for Secrets Store CSI Driver

| Metric           | Description                                            | Tags                                                                                                                                                    |
| ---------------- | ------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| keyvault_request | Distribution of how long it took to get from keyvault  | `os_type=<runtime os>`<br>`provider=azure`<br>`object_name=<keyvault object name>`<br>`object_type=<keyvault object type>`<br>`error=<error if failed>` |
| grpc_request     | Distribution of how long it took for the gRPC requests | `os_type=<runtime os>`<br>`provider=azure`<br>`grpc_method=<rpc full method>`<br>`grpc_code=<grpc status code>`<br>`grpc_message=<grpc status message>` |

Prometheus metrics are served from port 8898, but this port is not exposed outside the pod by default. Use kubectl port-forward to access the metrics over localhost:

```bash
kubectl port-forward ds/csi-secrets-store-provider-azure 8898:8898 &
curl localhost:8898/metrics
```

### Sample metrics output

```bash
# HELP grpc_request Distribution of how long it took for the gRPC requests
# TYPE grpc_request histogram
grpc_request_bucket{grpc_code="OK",grpc_message="",grpc_method="/v1alpha1.CSIDriverProvider/Mount",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.1"} 0
grpc_request_bucket{grpc_code="OK",grpc_message="",grpc_method="/v1alpha1.CSIDriverProvider/Mount",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.2"} 0
grpc_request_bucket{grpc_code="OK",grpc_message="",grpc_method="/v1alpha1.CSIDriverProvider/Mount",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.3"} 0
grpc_request_bucket{grpc_code="OK",grpc_message="",grpc_method="/v1alpha1.CSIDriverProvider/Mount",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.4"} 0
grpc_request_bucket{grpc_code="OK",grpc_message="",grpc_method="/v1alpha1.CSIDriverProvider/Mount",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.5"} 0
grpc_request_bucket{grpc_code="OK",grpc_message="",grpc_method="/v1alpha1.CSIDriverProvider/Mount",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="1"} 1
grpc_request_bucket{grpc_code="OK",grpc_message="",grpc_method="/v1alpha1.CSIDriverProvider/Mount",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="1.5"} 1
grpc_request_bucket{grpc_code="OK",grpc_message="",grpc_method="/v1alpha1.CSIDriverProvider/Mount",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="2"} 1
grpc_request_bucket{grpc_code="OK",grpc_message="",grpc_method="/v1alpha1.CSIDriverProvider/Mount",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="2.5"} 1
grpc_request_bucket{grpc_code="OK",grpc_message="",grpc_method="/v1alpha1.CSIDriverProvider/Mount",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="3"} 1
grpc_request_bucket{grpc_code="OK",grpc_message="",grpc_method="/v1alpha1.CSIDriverProvider/Mount",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="5"} 1
grpc_request_bucket{grpc_code="OK",grpc_message="",grpc_method="/v1alpha1.CSIDriverProvider/Mount",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="10"} 1
grpc_request_bucket{grpc_code="OK",grpc_message="",grpc_method="/v1alpha1.CSIDriverProvider/Mount",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="15"} 1
grpc_request_bucket{grpc_code="OK",grpc_message="",grpc_method="/v1alpha1.CSIDriverProvider/Mount",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="30"} 1
grpc_request_bucket{grpc_code="OK",grpc_message="",grpc_method="/v1alpha1.CSIDriverProvider/Mount",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="+Inf"} 1
grpc_request_sum{grpc_code="OK",grpc_message="",grpc_method="/v1alpha1.CSIDriverProvider/Mount",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0"} 0.935272626
grpc_request_count{grpc_code="OK",grpc_message="",grpc_method="/v1alpha1.CSIDriverProvider/Mount",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0"} 1
# HELP keyvault_request Distribution of how long it took to get from keyvault
# TYPE keyvault_request histogram
keyvault_request_bucket{error="",object_name="ingress-tls-pfx",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.1"} 0
keyvault_request_bucket{error="",object_name="ingress-tls-pfx",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.2"} 1
keyvault_request_bucket{error="",object_name="ingress-tls-pfx",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.3"} 1
keyvault_request_bucket{error="",object_name="ingress-tls-pfx",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.4"} 1
keyvault_request_bucket{error="",object_name="ingress-tls-pfx",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.5"} 1
keyvault_request_bucket{error="",object_name="ingress-tls-pfx",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="1"} 1
keyvault_request_bucket{error="",object_name="ingress-tls-pfx",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="1.5"} 1
keyvault_request_bucket{error="",object_name="ingress-tls-pfx",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="2"} 1
keyvault_request_bucket{error="",object_name="ingress-tls-pfx",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="2.5"} 1
keyvault_request_bucket{error="",object_name="ingress-tls-pfx",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="3"} 1
keyvault_request_bucket{error="",object_name="ingress-tls-pfx",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="5"} 1
keyvault_request_bucket{error="",object_name="ingress-tls-pfx",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="10"} 1
keyvault_request_bucket{error="",object_name="ingress-tls-pfx",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="15"} 1
keyvault_request_bucket{error="",object_name="ingress-tls-pfx",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="30"} 1
keyvault_request_bucket{error="",object_name="ingress-tls-pfx",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="+Inf"} 1
keyvault_request_sum{error="",object_name="ingress-tls-pfx",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0"} 0.127967922
keyvault_request_count{error="",object_name="ingress-tls-pfx",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0"} 1
keyvault_request_bucket{error="",object_name="secret1",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.1"} 0
keyvault_request_bucket{error="",object_name="secret1",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.2"} 0
keyvault_request_bucket{error="",object_name="secret1",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.3"} 0
keyvault_request_bucket{error="",object_name="secret1",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.4"} 0
keyvault_request_bucket{error="",object_name="secret1",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.5"} 0
keyvault_request_bucket{error="",object_name="secret1",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="1"} 1
keyvault_request_bucket{error="",object_name="secret1",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="1.5"} 1
keyvault_request_bucket{error="",object_name="secret1",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="2"} 1
keyvault_request_bucket{error="",object_name="secret1",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="2.5"} 1
keyvault_request_bucket{error="",object_name="secret1",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="3"} 1
keyvault_request_bucket{error="",object_name="secret1",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="5"} 1
keyvault_request_bucket{error="",object_name="secret1",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="10"} 1
keyvault_request_bucket{error="",object_name="secret1",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="15"} 1
keyvault_request_bucket{error="",object_name="secret1",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="30"} 1
keyvault_request_bucket{error="",object_name="secret1",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="+Inf"} 1
keyvault_request_sum{error="",object_name="secret1",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0"} 0.696671464
keyvault_request_count{error="",object_name="secret1",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0"} 1
keyvault_request_bucket{error="",object_name="secret2",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.1"} 0
keyvault_request_bucket{error="",object_name="secret2",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.2"} 1
keyvault_request_bucket{error="",object_name="secret2",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.3"} 1
keyvault_request_bucket{error="",object_name="secret2",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.4"} 1
keyvault_request_bucket{error="",object_name="secret2",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="0.5"} 1
keyvault_request_bucket{error="",object_name="secret2",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="1"} 1
keyvault_request_bucket{error="",object_name="secret2",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="1.5"} 1
keyvault_request_bucket{error="",object_name="secret2",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="2"} 1
keyvault_request_bucket{error="",object_name="secret2",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="2.5"} 1
keyvault_request_bucket{error="",object_name="secret2",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="3"} 1
keyvault_request_bucket{error="",object_name="secret2",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="5"} 1
keyvault_request_bucket{error="",object_name="secret2",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="10"} 1
keyvault_request_bucket{error="",object_name="secret2",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="15"} 1
keyvault_request_bucket{error="",object_name="secret2",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="30"} 1
keyvault_request_bucket{error="",object_name="secret2",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0",le="+Inf"} 1
keyvault_request_sum{error="",object_name="secret2",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0"} 0.107324667
keyvault_request_count{error="",object_name="secret2",object_type="secret",os_type="linux",provider="azure",service_name="csi-secrets-store-provider-azure",telemetry_sdk_language="go",telemetry_sdk_name="opentelemetry",telemetry_sdk_version="0.20.0"} 1
```