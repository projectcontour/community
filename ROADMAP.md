## Contour Roadmap

### About this document

This document provides a link to the [Contour Project board](https://github.com/orgs/projectcontour/projects/2) that serves as the up to date description of items that are in the Contour release pipeline. The board has separate swim lanes for releases and prioritized backlogs. Most items are gathered from the community or include a feedback loop with the community. This should serve as a reference point for Contour users and contributors to understand where the project is heading, and help determine if a contribution could be conflicting with a longer term plan. 

### How to help?

Discussion on the roadmap can take place in threads under [Issues](https://github.com/ProjectContour/Contour/issues) or in [community meetings](https://github.com/ProjectContour/community/blob/master/MEETING_SCHEDULE.md). Please open and comment on an issue if you want to provide suggestions and feedback to an item in the roadmap. Please review the roadmap to avoid potential duplicated efforts.

### How to add an item to the roadmap?
Please open an issue to track any initiative on the roadmap of Contour (Usually driven by new feature requests or [feature proposals](https://github.com/projectcontour/community/blob/master/GOVERNANCE.md#proposal-process)). For smaller enhancements, you can just open an issue to track that initiative or feature request. We work with and rely on community feedback to focus our efforts to improve Contour and maintain a healthy roadmap.

### Current Roadmap
The following table includes the current roadmap for Contour. If you have any questions or would like to contribute to Contour, please attend a [community meeting](https://projectcontour.io/community/) to discuss with our team. If you don't know where to start, we are always looking for contributors that will help us reduce technical, automation, and documentation debt.
Please take the timelines & dates as proposals and goals. Priorities and requirements change based on community feedback, roadblocks encountered, community contributions, etc. If you depend on a specific item, we encourage you to attend community meetings to get updated status information, or help us deliver that feature by contributing to Contour.

`Last Updated: July 2021`

|Theme|Description|Timeline|Issue|Notes|
|--|--|--|--|--|
|Observability|Support Access Log Service|2021 H2|[projectcontour/contour#1691](https://github.com/projectcontour/contour/issues/1691)||
|Gateway APIs|Introduce support for [upstream Gateway APIs](https://github.com/kubernetes-sigs/gateway-api)|2021 H2|[projectcontour/contour#2287](https://github.com/projectcontour/contour/issues/2287)|Contour will only support HTTPRoute and TLSRoute, the Layer 7 route objects. No support planned for TCPRoute and UDPRoute at this time.  Related issue that's on our radar - https://github.com/projectcontour/contour/issues/3367|
|Operational|Contour with managed Envoys|2021 H2||As part of the ongoing effort to support Gateway API, Contour will be managing the Envoy instances in a Contour deployment and existing ConfigMap representing the configuration will be redesigned as a CRD |
|Deployment|Contour Operator GA|2021 H2|[projectcontour/contour-operator#205](https://github.com/projectcontour/contour-operator/issues/205)|Bring the Operator to Beta release and then to GA release suitable for production environments. The Operator will fully support Contour leveraging Gateway API|
|General|Self Service Capabilities in Contour|2021 H2|[projectcontour/contour#2206](https://github.com/projectcontour/contour/issues/2206) mainly, with some others|It seems likely that some of these requests will be introduced by the Gateway APIs.|
|Infrastructure|Incorporate Envoy go-control-plane to modernize xDS|2021 H2|[projectcontour/contour#2134](https://github.com/projectcontour/contour/issues/2134)||
|Operational|Harden contour-authserver to provide a simple auth option|Unknown|[projectcontour/contour-authserver#14](https://github.com/projectcontour/contour-authserver/issues/14)|Contour-authserver is a small utility that translates between Envoy ext_auth gRPC and other protocols, this is to make it no longer experimental|
|Security|Add OIDC support to contour-authserver|Unknown|[projectcontour/contour-authserver#13](https://github.com/projectcontour/contour-authserver/pull/13)||
|Operational|Re-evaluate container image storage|2021 H2|[projectcontour/contour#3366](https://github.com/projectcontour/contour/issues/3366)|With the rate-limiting Dockerhub is applying, we need to decide if we will stay there or move to another container host.|
|Load Balancing|List of hash_policy for HTTPProxy|Unknown|[projectcontour/contour#3044](https://github.com/projectcontour/contour/issues/3044)||
|Security|IP Block list|Unknown|[projectcontour/contour#2971](https://github.com/projectcontour/contour/issues/2971)|Not sure if people want this one, will fill out our comparison with other ingress controllers.|
|Observability|Tracing support|2021 H2|[projectcontour/contour#399](https://github.com/projectcontour/contour/issues/399)|This triggered a deeper look at our existing ExtensionService and some possible changes might be needed|
|Operational|Session Affinity by Source IP|2021 H2|[projectcontour/contour#3703](https://github.com/projectcontour/contour/issues/3703)||
|Operational|Configurable circuit breaking|Unknown|[projectcontour/contour#1192](https://github.com/projectcontour/contour/issues/1192)||
|Tech Debt|Properly handle Envoy NACK messages|Unknown|[projectcontour/contour#1176](https://github.com/projectcontour/contour/issues/1176)||
|Testing|Improve Contour testing|Unknown|[projectcontour/contour#3312](https://github.com/projectcontour/contour/issues/3312)||
|New Use Case|UDP Support|Currently Won't Do|[projectcontour/contour#1248](https://github.com/projectcontour/contour/issues/1248)|Contour is currently focused on Layer 7 HTTP Ingress, and supports Layer 4 only in service of that goal. If you have use cases for UDP, please add them to the linked issue.|
|New Protocol|HTTP/3 or QUIC support|Unknown|[projectcontour/contour/#2582](https://github.com/projectcontour/contour/issues/2582)||




## Completed Roadmap items

|Theme|Description|Timeline|Issue|Notes|
|--|--|--|--|--|
|Security|FIPS Compliance|May 2021|
|General|Wildcard Hostname Matching|March 2021|[projectcontour/contour#2138](https://github.com/projectcontour/contour/issues/2138)|A limited form of this is required for both Ingress and Gateway-APIs.|
|Compatibility|Implement Kubernetes Ingress V1 specification (requires v1.16)|March 2021|[projectcontour/contour#2139](https://github.com/projectcontour/contour/issues/2139)||
|Performance|Rate limiting support|February 2021|[projectcontour/contour#370](https://github.com/projectcontour/contour/issues/370)| Local rate limiting support arrived in 1.12 in January 2021, global rate limiting support arrived in 1.13, February 2021.|
|Observability|Additional HTTPProxy Status information|October 2020|
|Security|Authentication support for services backed by Contour|October 2020|
|Extensibility|Expose more Envoy configuration knobs|December 2020|
|Infrastructure|xDS v3 upgrade|December 2020 (must be done by EOY 2020)|
|Deployment|Contour Helm Chart|December 2020|
|Operational|Contour Operator Alpha|December 2020|
