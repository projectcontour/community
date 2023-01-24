## Contour Roadmap

### About this document

This document provides a link to the [Contour Project board](https://github.com/orgs/projectcontour/projects/4) that serves as the up to date description of items that are in the Contour release pipeline.
The board tracks the Github milestones for upcoming releases and other issues planned to work on soon.
Most items are gathered from the community or include a feedback loop with the community.
This should serve as a reference point for Contour users and contributors to understand where the project is heading, and help determine if a contribution could be conflicting with a longer term plan.

### How to help?

Discussion on the roadmap can take place in threads under [Issues](https://github.com/projectcontour/contour/issues) or in [community meetings](https://github.com/ProjectContour/community/blob/master/MEETING_SCHEDULE.md).
Please open and comment on an issue if you want to provide suggestions and feedback to an item in the roadmap.
Please review the roadmap to avoid potential duplicated efforts.

### How to add an item to the roadmap?
Please open an issue to track any initiative on the roadmap of Contour (Usually driven by new feature requests or [feature proposals](https://github.com/projectcontour/community/blob/master/GOVERNANCE.md#proposal-process)).
For smaller enhancements, you can just open an issue to track that initiative or feature request.
We work with and rely on community feedback to focus our efforts to improve Contour and maintain a healthy roadmap.

### Current Roadmap
The following table includes the current roadmap for Contour.
If you have any questions or would like to contribute to Contour, please attend a [community meeting](https://projectcontour.io/community/) to discuss with our team.
If you don't know where to start, we are always looking for contributors that will help us reduce technical, automation, and documentation debt.
Please take the timelines & dates as proposals and goals.
Priorities and requirements change based on community feedback, roadblocks encountered, community contributions, etc.
If you depend on a specific item, we encourage you to attend community meetings to get updated status information, or help us deliver that feature by contributing to Contour.

`Last Updated: January 2023`

|Theme|Description|Timeline|Issue|Notes|
|--|--|--|--|--|
|Gateway API|Implement GRPCRoute|2023 H1|[projectcontour/contour#4820](https://github.com/projectcontour/contour/issues/4820)|Work has started on a design document for this feature.|
|Gateway API|Support arbitrary number of Listeners per-Gateway|2023 H1|[projectcontour/contour#4960](https://github.com/projectcontour/contour/issues/4960)|Will likely be required to stay conformant with Gateway API.|
|Observability|Tracing support|2023 H1|[projectcontour/contour#399](https://github.com/projectcontour/contour/issues/399)|Work has started on a design document for this feature.|
|Security|IP Block list|2023 H1|[projectcontour/contour#2971](https://github.com/projectcontour/contour/issues/2971) and [projectcontour/contour#3693](https://github.com/projectcontour/contour/issues/3693)|Work has started on a design document for this feature.|
|Infrastructure|Replace Contour xDS code with go-control-plane as default|2023 H2|[projectcontour/contour#2134](https://github.com/projectcontour/contour/issues/2134)|There’s some work left to do, but this should be finished soon.These changes will also make Delta xDS available, which should help with wire transfer times and scalability.|
|Security|Add OIDC support to contour|Unknown|[projectcontour/contour#2664](https://github.com/projectcontour/contour/issues/2664)|This covers work to pull OIDC support directly into Contour, without requiring running an external auth server. We started this work, but the Oauth2 filter in Envoy is still very experimental and needs a lot of work. This work can’t proceed until significant work has been done on the Oauth2 filter.|
|New Use Case|UDP Support|Won't Do|[projectcontour/contour#1248](https://github.com/projectcontour/contour/issues/1248)|Contour is focused on Layer 7 HTTP Ingress, and supports Layer 4 only in service of that goal. Contour will not add UDP support.|



## Completed Roadmap items

|Theme|Description|Timeline|Issue|Notes|
|--|--|--|--|--|
|Gateway API|Create a plan for v0.6.0|2022 H2| [projectcontour/contour#4738](https://github.com/projectcontour/contour/issues/4738)|Make a plan for how to handle Gateway API v0.6.0 when it's released.|
|Operational|Contour with managed Envoys|2022 H1||Contour’s Gateway API implementation now allows for the dynamic creation of Envoy Daemonsets or Deployments, this functionality is included there.We were considering making this available outside of Gateway API, but the work involved is too prohibitive.|
|Gateway APIs|Implement Gateway 0.5.0 API Support|2021 H2|[projectcontour/contour#2287](https://github.com/projectcontour/contour/issues/2287)|Contour will only support HTTPRoute and TLSRoute, the Layer 7 route objects. No support planned for TCPRoute and UDPRoute at this time.  Related issue that's on our radar - https://github.com/projectcontour/contour/issues/3367|
|Deployment|Contour Operator GA|Won't do|[projectcontour/contour-operator#205](https://github.com/projectcontour/contour-operator/issues/205)|The Operator will not be moved to GA. It’s now in maintenance mode, and will have minimal updates done to keep it working with new Contour releases until we say otherwise. Once Envoy Gateway is available and ready for use, we strongly encourage Operator users to move to it for your dynamic ingress traffic routing needs.|
|Operational|Harden contour-authserver to provide a simple auth option|Won't do|[projectcontour/contour-authserver#14](https://github.com/projectcontour/contour-authserver/issues/14)|Contour-authserver is an experimental ext_auth server. We’re going to move this to archived, as we don’t expect further development on it. https://github.com/travisghansen/external-auth-server is a possible alternative.| Envoy Gateway definitely wants to build this, it requires work to build into the Gateway API, then work to implement external auth. Inline auth for Envoy Gateway is a separate issue, that also has a lot of interest there.
|Load Balancing|List of hash_policy for HTTPProxy|Unknown|[projectcontour/contour#3044](https://github.com/projectcontour/contour/issues/3044)||
|Operational|Session Affinity by Source IP|2021 H2|[projectcontour/contour#3703](https://github.com/projectcontour/contour/issues/3703)|Implemented in [#4141](https://github.com/projectcontour/contour/pull/4141)|
|Operational|Re-evaluate container image storage|2021 H2|[projectcontour/contour#3366](https://github.com/projectcontour/contour/issues/3366)|Contour's primary image storage has moved to Github Container Registry (GHCR)|
|Security|FIPS Compliance|May 2021|
|General|Wildcard Hostname Matching|March 2021|[projectcontour/contour#2138](https://github.com/projectcontour/contour/issues/2138)|A limited form of this is required for both Ingress and Gateway-APIs.|
|Compatibility|Implement Kubernetes Ingress V1 specification (requires v1.16)|March 2021|[projectcontour/contour#2139](https://github.com/projectcontour/contour/issues/2139)||
|Performance|Rate limiting support|February 2021|[projectcontour/contour#370](https://github.com/projectcontour/contour/issues/370)| Local rate limiting support arrived in 1.12 in January 2021, global rate limiting support arrived in 1.13, February 2021.|
|General|Self Service Capabilities in Contour|2021 H2|[projectcontour/contour#2206](https://github.com/projectcontour/contour/issues/2206) mainly, with some others|See #2206, but in short, HTTPProxy and self-service don't work. The Gateway API has been better desgined to be able to support this sort of capability, and will be the method via which this solved. There's nothing more for Contour to do here.|
|Observability|Additional HTTPProxy Status information|October 2020|
|Security|Authentication support for services backed by Contour|October 2020|
|Extensibility|Expose more Envoy configuration knobs|December 2020|
|Infrastructure|xDS v3 upgrade|December 2020 (must be done by EOY 2020)|
|Deployment|Contour Helm Chart|December 2020|
|Operational|Contour Operator Alpha|December 2020|
