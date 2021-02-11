# Organization of work in Magma development

## Workstreams

Workstreams in Magma are subgroups focused on delivering a set of features.
They are comparable to SIGs in other projects.

All workstreams report to a common weekly engineering meeting:

* Meeting: Thursday 16:30 UTC
* Meeting notes: [etherpad](https://etherpad.opendev.org/p/magmaweekly_notes)

### Workstream 1: Applications and Services

* Leads: Ulas Kozat & Phil Ritter
* Meeting: Weekly on Monday 8:30am PT

### Workstream 2: Orchestration

* Lead: Parthiban Nalliamudali
* Meeting: Monday 5:30 PT

### Workstream 3: Automation / Continuous Integration

* Lead: Boris Renski
* Meeting: Weekly (Thursday 17:30 UTC)
* Meeting notes: [etherpad](https://etherpad.opendev.org/p/magma_workstream3)

## Roles

### Contributors

Anyone can become a Contributor by submitting a pull request to the project
and having that change accepted through the project’s review process. A
Contributor is someone who has had code merged within the last 12 months.
Contributors are eligible to vote in governance elections. Contributors have
access to propose and review code but not merge the code into repos of the
project.

### Maintainers

A Maintainer has the ability to merge code into the project. Maintainers are
active Contributors and participants in the project. In order to become a
Maintainer, you must be nominated and approved by the established Maintainers,
through a simple majority vote with no existing maintainer objecting.
Within the project, sub-components may decide to have additional requirements
for the review of code in their repos.

#### magma/magma repository

Magma development work uses this single git repository, which uses a Maintainer
group (who can approve code for merging) and a
[CODEOWNERS](https://github.com/magma/magma/blob/master/CODEOWNERS) file
(required code review before merging).

Maintainers:

* Amar Padmanabhan (@amarpad)
* Michael Callahan (@mcallahan)
* Michael Germano (@mpgermano)
* Shruti Sanadhya (@ssanadhya)
* Marie Themarwhal (@themarwhal)
* Timothee Dzik (@tmdzk)
* Ulas Kozat (@ulaskozat)
* Vitalli Kostenko (@119Vik)
* Aharon Novogrodksi (@aharonnovo)
* Andrei Lee (@andreilee)
* Alex Rodriguez (@ardzoht)
* AyliD (@AyliD)
* Scott Moeller (@electronjoe)
* Evgeniy Makaeev (@emakeev)
* HannaFar (@HannaFar)
* Hunter Gatewood (@hcgatewood)
* Karthik Subraveti (@karthiksubraveti)
* Mykola Yurchenko (@koolzz)
* Matthew Mosesohn (@mattymo)
* r-i-g (@r-i-g)
* Philip Ritter (@PARitter)
* Pravin Shelar (@pshelar)
* Raphael Deffosseux (@rdefosse)
* Oriol Batalla (@uri200)
* Ekow Taylor (@ekowtaylor)
* Ken Khars (@kkahrs)
* Scott Smith (@Scott8440)
* Youssef El Masmoudi (@ymasmoudi)

#### magma/community repository

This repository contains community and governance rules for the Magma project.
It is currently maintained by the magma GitHub org admins. Once the Magma TC
is elected, it should be maintained by a Maintainer group, which should match
the TC membership.

#### magma/magma-website repository

This repository contains code and resources for the magmacore.io website.
This only uses a Maintainer group.

Maintainers:

* Jonathan Bryce (@jbryce)
* Wes Wilson (@iamweswilson)
* Jimmy McArtur (@jimmytipit)
