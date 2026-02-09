# Philanthropy Data Commons: Service Instances

Below is a list of the PDC service instances we maintain.  Each PDC
service instance uses a separate database and a separate S3 bucket.

* **Production API**: https://api.philanthropydatacommons.org/

  This is the production instance of the PDC Framework API server.
  This instance holds real data, and authenticates users against the
  production instance of Keycloak
  (`auth.philanthropydatacommons.org`).

* **Production App**: https://app.philanthropydatacommons.org/

  An instance of PDC Framework administrative application that runs
  against the Production API service.

* **Staging API**: https://api-test.philanthropydatacommons.org/

  (a.k.a. "QA", "demo", "test", "sandbox")

  This is the staging instance for the PDC Framework API.  This
  instance holds dummy data, except that its baseField data is copied
  from Production regularly (at least daily).  Staging authenticates
  users against the staging instance of Keycloak
  (`auth-test.philanthropydatacommons.org`).

  TBD: We have historically had sandbox instances with funny names
  like those mentioned in [this 2025-10-25 Zulip message from
  Karl](https://chat.opentechstrategies.com/#narrow/channel/75-PDC/topic/infrastructure/near/242528).
  Do we still have those?  We want to get away from funny URLs and
  move toward standardized places to deploy things for tire-kicking,
  to the extent that Staging doesn't suffice for that.

* **Staging App**: https://app-test.philanthropydatacommons.org/

  An instance of PDC Framework administrative application that runs
  against the Staging API service.

* **Dev**: 

  TBD: Do we have any dev instances right now?  Of either API server
  or app server or both?  If so, what are their URLs?

  (See the 2026-01-20 entry
  [here](https://pad.opentechstrategies.com/p/pdc-dev-meetings-2026)
  for more context.)

TBD See the latest [diagram from
Jesse](https://chat.opentechstrategies.com/#narrow/channel/75-PDC/topic/extra.20environments/near/251816)
as of 2026-02-03, and surrounding conversation (including [this
one](https://chat.opentechstrategies.com/#narrow/channel/75-PDC/topic/extra.20environments/near/250885))
for what we're sorting out here.
