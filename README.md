# Philanthropy Data Commons: Data and Software Development Practices

A repository for PDC-wide discussion, documentation, and assets.

As a baseline, [PDC software
projects](https://github.com/PhilanthropyDataCommons/) follow the
coding and developer community guidelines [listed
here](https://code.librehq.com/ots/meta), but individual PDC project
repositories may have additional guidelines that supersede those.
Please consult the documentation for the particular project you're
working in.

For information about what service instances this project uses (e.g.,
production, staging, etc), please see [INSTANCES.md](INSTANCES.md).

For policies about data management, please see
[POLICIES.md](POLICIES.md).

## Overview

Visit https://philanthropydatacommons.org/ for a high-level overview of the PDC.

## Accessing Data in the Philanthropy Data Commons Using the API

This section describes using the PDC API to view or send data to the PDC. There
may be multiple ways to accomplish this in future.

To use the PDC API to view changemaker data, see the [OpenAPI documentation for
the `GET /changemakers` endpoint
](https://api.philanthropydatacommons.org/#/Changemakers/getChangemakers). No
authentication is required to view changemaker data.

To see more data or add data to the Philanthropy Data Commons, you will need a
User in the PDC system. Please use the [Contact
form](https://philanthropydatacommons.org/contact/) to describe your PDC user
story and that you would like to be added to the PDC.

## Sending Data to the Philanthropy Data Commons Using the API

Get a User that can log in as described above.

Familiarize yourself with the central PDC service API by visiting the [OpenAPI
documentation at the PDC](https://api.philanthropydatacommons.org). The related
[(aspirational) Entity Relation Diagram
](https://github.com/PhilanthropyDataCommons/service/blob/main/docs/ENTITY_RELATIONSHIP_DIAGRAM.md)
helps see how data are modeled.

Use the "Authorize" button in the upper right and click "Authorize" again (no
changes on the form are needed) to log in to the PDC.

Use the [`POST /proposalVersions` endpoint
](https://api.philanthropydatacommons.org/#/Proposals/addProposalVersion)
to add data. Of course, there are multiple other things to add prior to using
this endpoint, as you can see in the required parameters here and the required
parameters of the related endpoints.
