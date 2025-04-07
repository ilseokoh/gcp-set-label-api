# GCP set Label API 

## VPN
### 1. labelFingerprint 가져오기 

[https://cloud.google.com/compute/docs/reference/rest/v1/vpnGateways/get](https://cloud.google.com/compute/docs/reference/rest/v1/vpnGateways/get)

```bash
curl -X GET \
-H "Authorization: Bearer $(gcloud auth print-access-token)" \
"https://compute.googleapis.com/compute/v1/projects/kevin-gcp-456101/regions/us-west1/vpnGateways/on-prem-vpn-gw1"
```

```bash
{
  "kind": "compute#vpnGateway",
  "id": "6960792223438770848",
  "creationTimestamp": "2025-04-06T18:37:19.172-07:00",
  "name": "on-prem-vpn-gw1",
  "region": "https://www.googleapis.com/compute/v1/projects/kevin-gcp-456101/regions/us-west1",
  "network": "https://www.googleapis.com/compute/v1/projects/kevin-gcp-456101/global/networks/on-prem",
  "selfLink": "https://www.googleapis.com/compute/v1/projects/kevin-gcp-456101/regions/us-west1/vpnGateways/on-prem-vpn-gw1",
  "labels": {
    "owner": "eswa"
  },
  "labelFingerprint": "7CnT0csvdyM=",
  "vpnInterfaces": [
    {
      "id": 0,
      "ipAddress": "34.157.114.246"
    },
    {
      "id": 1,
      "ipAddress": "35.220.52.193"
    }
  ],
  "stackType": "IPV4_ONLY",
  "gatewayIpVersion": "IPV4"
}
```

### 2. vpnGateways.setLabels 

[https://cloud.google.com/compute/docs/reference/rest/v1/vpnGateways/setLabels](https://cloud.google.com/compute/docs/reference/rest/v1/vpnGateways/setLabels)

```bash
curl -X POST \
"https://compute.googleapis.com/compute/v1/projects/kevin-gcp-456101/regions/us-west1/vpnGateways/on-prem-vpn-gw1/setLabels" \
-H "Authorization: Bearer $(gcloud auth print-access-token)" \
-H "Content-Type: application/json" \
-d '{"labelFingerprint": "7CnT0csvdyM=", "labels": {"owner1": "eswa1"}}'
```

```
{
  "kind": "compute#operation",
  "id": "4967277350499549869",
  "name": "operation-1743993922353-632273a3b7b3d-963a3261-0d811ec4",
  "operationType": "setLabels",
  "targetLink": "https://www.googleapis.com/compute/v1/projects/kevin-gcp-456101/regions/us-west1/vpnGateways/on-prem-vpn-gw1",
  "targetId": "6960792223438770848",
  "status": "DONE",
  "user": "admin@iloh.altostrat.com",
  "progress": 100,
  "insertTime": "2025-04-06T19:45:22.535-07:00",
  "startTime": "2025-04-06T19:45:22.535-07:00",
  "endTime": "2025-04-06T19:45:22.535-07:00",
  "selfLink": "https://www.googleapis.com/compute/v1/projects/kevin-gcp-456101/regions/us-west1/operations/operation-1743993922353-632273a3b7b3d-963a3261-0d811ec4",
  "region": "https://www.googleapis.com/compute/v1/projects/kevin-gcp-456101/regions/us-west1"
}
```

### 3. vpnTunnels.get

[https://cloud.google.com/compute/docs/reference/rest/v1/vpnTunnels/get](https://cloud.google.com/compute/docs/reference/rest/v1/vpnTunnels/get)

```bash
curl -X GET \
-H "Authorization: Bearer $(gcloud auth print-access-token)" \
"https://compute.googleapis.com/compute/v1/projects/kevin-gcp-456101/regions/us-west1/vpnTunnels/on-prem-tunnel0"
```

```
{
  "kind": "compute#vpnTunnel",
  "id": "8838319958361281410",
  "creationTimestamp": "2025-04-06T18:42:05.376-07:00",
  "name": "on-prem-tunnel0",
  "description": "",
  "region": "https://www.googleapis.com/compute/v1/projects/kevin-gcp-456101/regions/us-west1",
  "vpnGateway": "https://www.googleapis.com/compute/v1/projects/kevin-gcp-456101/regions/us-west1/vpnGateways/on-prem-vpn-gw1",
  "vpnGatewayInterface": 0,
  "peerGcpGateway": "https://www.googleapis.com/compute/v1/projects/kevin-gcp-456101/regions/us-west1/vpnGateways/vpc-demo-vpn-gw1",
  "router": "https://www.googleapis.com/compute/v1/projects/kevin-gcp-456101/regions/us-west1/routers/on-prem-router1",
  "peerIp": "34.157.117.141",
  "sharedSecret": "*************",
  "sharedSecretHash": "QOumhYnFh4FajP1W2LDX9t2ZgPZT",
  "status": "ESTABLISHED",
  "selfLink": "https://www.googleapis.com/compute/v1/projects/kevin-gcp-456101/regions/us-west1/vpnTunnels/on-prem-tunnel0",
  "ikeVersion": 2,
  "detailedStatus": "Tunnel is up and running.",
  "localTrafficSelector": [
    "0.0.0.0/0"
  ],
  "remoteTrafficSelector": [
    "0.0.0.0/0"
  ],
  "labels": {
    "cost_center": "1111",
    "workload": "network"
  },
  "labelFingerprint": "9fUPpV31eCY="
}
```

### 4. vpnTunnels.setLabels

```bash
curl -X POST \
"https://compute.googleapis.com/compute/v1/projects/kevin-gcp-456101/regions/us-west1/vpnTunnels/on-prem-tunnel0/setLabels" \
-H "Authorization: Bearer $(gcloud auth print-access-token)" \
-H "Content-Type: application/json" \
-d '{"labelFingerprint": "9fUPpV31eCY=", "labels": {"owner1": "eswa1"}}'
```

```

  "kind": "compute#operation",
  "id": "5309100496074505870",
  "name": "operation-1743994977871-63227792564f5-576bdaaf-74835234",
  "operationType": "setLabels",
  "targetLink": "https://www.googleapis.com/compute/v1/projects/kevin-gcp-456101/regions/us-west1/vpnTunnels/on-prem-tunnel0",
  "targetId": "8838319958361281410",
  "status": "DONE",
  "user": "admin@iloh.altostrat.com",
  "progress": 100,
  "insertTime": "2025-04-06T20:02:57.912-07:00",
  "startTime": "2025-04-06T20:02:57.925-07:00",
  "endTime": "2025-04-06T20:02:57.926-07:00",
  "selfLink": "https://www.googleapis.com/compute/v1/projects/kevin-gcp-456101/regions/us-west1/operations/operation-1743994977871-63227792564f5-576bdaaf-74835234",
  "region": "https://www.googleapis.com/compute/v1/projects/kevin-gcp-456101/regions/us-west1"
}
```
