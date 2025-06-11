# Base Field Admin

We want to create an interface for PDC admins to manage base fields. It needs to allow:

- Viewing base fields in the database
- Drilling in to a single base field
- Editing the base field attributes ([see the BaseField type](https://github.com/PhilanthropyDataCommons/service/blob/main/src/types/BaseField.ts))
- Communicating to the user preemptively that some editing choices (e.g. changing short code or sensitivity) have destructive or breaking ramifications
- Adding new base fields

The team discussed the scope and requirements at meetings which were documented [in this pad](https://pad.opentechstrategies.com/p/pdc-admin-ui-design-2025-05-23).
