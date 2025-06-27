# Bulk Uploader

We need to design and build a new bulk uploader using what we learned on the existing one, adapting to the latest data models and entities, and adding sensible features.

Justin Reese and Jonathan Mergy worked together on desired scope and requirements for this uploader. ([Read notes from that session.](https://pad.opentechstrategies.com/p/Bulk_Upload_Requirements))

**Target user:** PDC operations team member. (**Not** changemakers, funders, or other external users.)

## MVP Requirements

- Log in with Keycloak credentials
- Upload a CSV of proposal rows, keyed by base field shortCodes, which contains any necessary association IDs (source ID, application form ID) to correctly create a proposal
  - A "so nice to have that we should strongly consider it as MVP" feature is to omit the association IDs from the CSV, and instead allow the user to select from a list of sources, application forms, and other associated entities prior to upload
- Where the uploader identifies an existing proposal in the system, it should create a new version
- If any errors are encountered, the entire operation is transactionally cancelled (see ④ below for an optional different mode)
- Both successful and unsuccessful uploads should generate a report of what happened: number of records added, timestamp, any useful identifiers like a job ID, etc.
- View list of prior uploads
- View list of base fields for reference (see ③ for scope of base fields to show)

## Stretch Goals / Post-MVP Enhancements

1. Rather than requiring associated object IDs (sources, application forms, etc.) in the CSV, let users select from a drop-down list prior to upload. E.g., select sources, then select application forms for those sources, then upload the CSV.
2. Allow users to create new sources, application forms, and other prerequisite entities prior to upload.
3. After selecting sources or application forms, filter the base field reference to only those base fields that are relevant to that context (and limit the CSV as well). Also display any custom labels for that base field on that application form.
4. Provide an option to the user for how to handle errors: stop and transactionally cancel (default), or skip problem row and continue?
   - Would need to enhance the report to detail which rows succeeded and which didn't, probably with a download of the original CSV with a new success/fail indication column.
5. Provide an option to the user for how to handle duplicate proposal IDs: create a new version of the existing proposal (default), or treat as an error (skip creation)?

## User stories (by Jonathan Mergy)

- As a PDC Ops team member, I want to be able to login to a web interface for the PDC Framework where I can access the Bulk Upload function.
- As a PDC Ops team member, I wand to be able to select the required data elements to properly associate bulk uploaded data to API endpoints of Source, appForm, Proposal, Proposal version and other related and required elements of PDC Framework data.
- As a PDC Ops team member, I want to be able to upload a number of records in CSV format into PDC and mimicking the methodology data comes into via the API directly
- As a PDC Ops team member, I want to be able to create a new pdc source in the bulk upload interface for my bulk upload
- As a PDC Ops team member, I want to be able to create a new funder record in the bulk upload interface for my bulk upload
- As a PDC Ops team member, I want to be able to create a new appForm through selection of existing baseFields via a menu or some manner to great a new record to reference in the bulk upload interface to use for my bulk upload
- As a PDC Ops team member, I want to be able to create a new proposal record in the bulk upload interface to select for my bulk upload data.
- As a PDC Ops team member, I want to be able to provide proposalId as one of the columns in my csv for bulk upload that the bulk upload function will use for proposalVersions
- As a PDC Ops team member, I want to have bulk upload generate proposalIds if I don't have a columnin my csv in my data and the bulk upload function will use the generated values for proposalVersions
- As a PDC Ops team member, I want to be able to have the bulk upload function associate proposal versions to existing changemakers in the PDC Framework data if they exist, or create new organizations if they do not.
- As a PDC Ops team member, I want to be able to leverage the data categories in the PDC Framework associated with the baseFields for the data in my bulk upload so my data is properly placed into the data categories.
- As a PDC Ops team member, I want to be able to have all data from my bulk upload data be uploaded to a single set/combination of PDC Framework source, appForm. Proposal, etc. (we don't need bulk upload to handle multiple sources, appForms, yet -- we will just do multiple passes initially.)
- As a PDC Ops team member, I want to have an option in the bulk upload interface to set how errors or record/rows should fail. Default should be if any errors are hit, none of the data is uploaded. But, should allow user to change the default to allow partial upload of rows that can be uploaded and omit failed records.
