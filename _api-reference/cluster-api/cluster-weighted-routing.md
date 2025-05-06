---
layout: default
title: Cluster weighted routing
nav_order: 60
parent: Cluster APIs
---

# Cluster weighted routing
**Introduced 1.0**
{: .label .label-purple }

The Cluster Weighted Routing API creates or updates routing weights for shard allocation.

# Endpoints

The `GET` method fetches shard routing weights.

<!-- spec_insert_start
api: cluster.get_weighted_routing
component: endpoints
omit_header: true
-->
```json
GET /_cluster/routing/awareness/{attribute}/weights
```
<!-- spec_insert_end -->

The `PUT` method updates shard routing weights.

<!-- spec_insert_start
api: cluster.put_weighted_routing
component: endpoints
omit_header: true
-->
```json
PUT /_cluster/routing/awareness/{attribute}/weights
```
<!-- spec_insert_end -->

The `DELETE` method deletes shard routing weights.

<!-- spec_insert_start
api: cluster.delete_weighted_routing
component: endpoints
omit_header: true
-->
```json
DELETE /_cluster/routing/awareness/weights
```
<!-- spec_insert_end -->

<!-- spec_insert_start
api: cluster.put_weighted_routing
component: path_parameters
-->
## Path parameters

The following table lists the available path parameters.

| Parameter | Required | Data type | Description |
| :--- | :--- | :--- | :--- |
| `attribute` | **Required** | String | The name of awareness attribute, usually `zone`. |

<!-- spec_insert_end -->

## Example request

```json
PUT /_cluster/routing/awareness/zone/weights
{
  "weights": {
    "zone-1": 3,
    "zone-2": 2,
    "zone-3": 1
  }
}
```
{% include copy-curl.html %}

## Example response

```json
{
  "acknowledged": true,
  "persistent": {
    "cluster": {
      "routing": {
        "awareness": {
          "zone": {
            "weights": {
              "zone-1": "3",
              "zone-2": "2",
              "zone-3": "1"
            }
          }
        }
      }
    }
  },
  "transient": {}
}
```