# Contour Governance

This document defines the project governance for Contour.

## Overview

**Contour**, an open source project, is committed to building an open, inclusive, productive and self-governing open source community focused on building a high-quality and high performance ingress controller for Kubernetes. The community is governed by this document with the goal of defining how community should work together to achieve this goal.

## Code Repositories

All the code repositories owned by the Project Contour GitHub Organization are
governed by Contour community and maintained under the `ProjectContour` namespace.
The following repos are the most noteworthy:

* **[Contour](https://github.com/projectcontour/contour):** Main Contour codebase.
* **[community](https://github.com/projectcontour/community):** Used to store community-related material–e.g., proposals, presentation slides, governance documents, community meeting minutes, etc.
* **[contour-operator](https://github.com/projectcontour/contour-operator):** The Contour Operator is a tool for installing and managing Contour.

## Community Roles

All of the below roles share the responsibility to abide by the Code of Conduct and work together towards making the project better.

* **Users:** Members that engage with the Contour community via any medium (Slack, GitHub, mailing lists, etc.).
* **Contributors:** Regular contributions to projects (documentation, code reviews, responding to issues, participation in proposal discussions, contributing code, etc.). 
* **Reviewer:** Review contributions from other members.
* **Maintainers**: The Contour project leaders. They are responsible for the overall health and direction of the project; final reviewers of PRs and responsible for releases. 
* **SIG members/owner**: Members of a specific SIG are responsible for the work within that SIG topic, and SIG owners are responsible for driving the efforts within a SIG.

### Reviewer
Reviewers are able to review code for quality and correctness on some part of a subproject. They are knowledgeable about both the codebase and software engineering principles.

#### Requirements

* Knowledgeable about the codebase
* Sponsored by a maintainer
* New reviewer must be nominated by an existing maintainer or reviewer or self-nominated and must be elected by a supermajority of existing maintainers

#### Responsibilities and privileges

* Code reviewer status may be a precondition to accepting large code contributions
* Responsible for project quality control via code reviews
* Focus on code quality and correctness, including testing and factoring
* May also review for more holistic issues, but not a requirement
* Expected to be responsive to review requests
* Assigned PRs to review related to subproject of expertise
* Assigned test bugs related to subproject of expertise

### Maintainers

New maintainers must be nominated by an existing maintainer and must be elected by a supermajority of existing maintainers. Likewise, maintainers can be removed by a supermajority of the existing maintainers or can resign by notifying one of the maintainers.

#### Maintainer Expectations

Maintainers have the ability to merge code into the project.
Anyone is eligible to become an maintainer see Becoming a maintainer below.

As such, there are certain expectations for maintainers. Contour maintainers
are expected to:

* Review pull requests, triage issues, and fix bugs in their areas of expertise, ensuring that all changes go through the project's code review and integration processes.
* Monitor cncf-contour-* emails and the Contour Slack, and help out when possible.
* Rapidly respond to any time-sensitive security release processes.

Some Maintainers are responsible for one or more components within a project, acting as technical leads for that component. Maintainers are expected to contribute code and documentation, review PRs including ensuring quality of code, triage issues, proactively fix bugs, and perform maintenance tasks for these components.

If a maintainer is no longer interested in or cannot perform the duties
listed above, they should move themselves to emeritus status. If necessary,
this can also occur through the decision-making process outlined below.


#### Becoming a maintainer

* Anyone is eligible to become a Contour maintainer
* Maintainers should be proficient in Go
* have relevant domain expertise
* have the time and ability to meet the maintainer expectations above
* and demonstrate the ability to work with the existing maintainers and project processes

*New maintainers must be nominated by an existing maintainer and must be elected by a supermajority of existing maintainers. Likewise, maintainers can be removed by a supermajority of the existing maintainers or can resign by notifying one of the maintainers.*

### SIGs and SIG-owner

SIGs oversee and coordinate the interests and needs of end users and projects in a particular area. By definition, they are long-lived groups that coordinate their work with the maintainers team and are led primarily by recognized experts in the relevant field and supported by other contributors.

### Supermajority

A supermajority is defined as two-thirds of members in the group.
A supermajority of [Maintainers](#maintainers) is required for certain
decisions as outlined above. Voting on decisions can happen on the mailing list, GitHub, Slack, email, or via a voting service, when appropriate. Maintainers can either vote "agree, yes, +1", "disagree, no, -1", or "abstain". A vote passes when supermajority is met. An abstain vote equals not voting at all.

### Decision Making

Ideally, all project decisions are resolved by consensus. If impossible, any
maintainer may call a vote. Unless otherwise specified in this document, any
vote will be decided by a supermajority of maintainers.

Votes by maintainers belonging to the same company
will count as one vote; e.g., 4 maintainers employed by fictional company **Contorsium** will
only have **one** combined vote. If voting members from a given company do not
agree, the company's vote is determined by a supermajority of voters from that
company. If no supermajority is achieved, the company is considered to have
abstained.

## Proposal Process

One of the most important aspects in any open source community is the concept
of proposals. Large changes to the codebase and / or new features should be
preceded by a proposal in our community repo. This process allows for all
members of the community to weigh in on the concept (including the technical
details), share their comments and ideas, and offer to help. It also ensures
that members are not duplicating work or inadvertently stepping on toes by
making large conflicting changes.

The project roadmap is defined by accepted proposals.

Proposals should cover the high-level objectives, use cases, and technical
recommendations on how to implement. In general, the community member(s)
interested in implementing the proposal should be either deeply engaged in the
proposal process or be an author of the proposal.

The proposal should be documented as a separated markdown file pushed to the root of the 
`design` folder in the [Contour](https://github.com/projectcontour/contour/tree/master/design)
repository via PR. The name of the file should follow the name pattern `<short
meaningful words joined by '-'>_design.md`, e.g:
`listener-design.md`.

Use the [Proposal Template](https://github.com/projectcontour/contour/blob/master/design/design-document-tmpl.md) as a starting point.

### Proposal Lifecycle

The proposal PR can be marked with different status labels to represent the
status of the proposal:

* **Draft**: Proposal is just created.
* **Reviewing**: Proposal is under review and discussion.
* **Accepted**: Proposal has been reviewed and is accepted (either by consensus or through a vote).
* **Declined**: Proposal has been reviewed and was rejected (either by consensus or through a vote).

### Lazy Consensus

To maintain velocity in a project as busy as Contour, the concept of [Lazy
Consensus](http://en.osswiki.info/concepts/lazy_consensus) is practiced. Ideas
and / or proposals should be shared by maintainers via
GitHub with the appropriate maintainer groups (e.g.,
`@ProjectContour/maintainers`) tagged. Out of respect for other contributors,
major changes should also be accompanied by a ping on Slack or a note on the
Contour dev mailing list as appropriate. Author(s) of proposal, Pull Requests,
issues, etc.  will give a time period of no less than five (5) working days for
comment and remain cognizant of popular observed world holidays.

Other maintainers may chime in and request additional time for review, but
should remain cognizant of blocking progress and abstain from delaying
progress unless absolutely needed. The expectation is that blocking progress
is accompanied by a guarantee to review and respond to the relevant action(s)
(proposals, PRs, issues, etc.) in short order.

Lazy Consensus is practiced for all projects in the `ProjectContour` org, including
the main project repository, community-driven sub-projects, and the community
repo that includes proposals and governing documents.

Lazy consensus does _not_ apply to the process of:

* Removal of maintainers from Contour

## Updating Governance

All substantive changes in Governance require a supermajority agreement by all maintainers.


## Thanks

Many thanks in advance to everyone who contributes their time and effort to making Contour both a successful system as well as a successful community. The strength of our software shines in the strengths of each individual community member.
Thanks!

**Some content in this document were built(inspired) upon the work in the [Kubernetes](https://github.com/kubernetes/community), [Linkerd](https://github.com/linkerd/linkerd2/blob/main/GOVERNANCE.md), [Helm](https://github.com/helm/community/blob/main/governance) Communities! KUDOs to all of them!**