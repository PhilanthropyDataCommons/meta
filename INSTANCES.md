# Philanthropy Data Commons: Apps and Environments

Below is a list of the PDC applications OTS maintains.

- **API**: https://api.philanthropydatacommons.org/

  This is the production instance of the PDC Framework API server.
  This instance holds real data, and authenticates users against the
  production instance of Keycloak (see "Auth" below).

- **App (non-admin)**: https://app.philanthropydatacommons.org/

  An instance of PDC Framework non-administrative application suite that runs
  against the Production API service. It authenticates users via the production
  instance of Keycloak. The proposal bulk uploader is here.

- **Admin App**: https://admin.philanthropydatacommons.org/

  An instance of PDC Framework administrative application suite that runs
  against the Production API service. It authenticates users via the
  production instance of Keycloak. The base fields editor is here.

- **Auth**: https://auth.philanthropydatacommons.org/realms/pdc/account

  An instance of Keycloak manages users and their respective organization
  integrations. Users authenticate here or are redirected to their organization
  authentication providers by Keycloak. Keycloak does not enforce authorization
  to PDC data. Authorization (as opposed to authentication) is handled within
  API instance databases using a reference to Keycloak users and organizations.
  All PDC applications are expected to use Keycloak for authentication.

## Additional Environments and Instances

Additional environments (and instances in them) are for special purposes. In
general, if you are not developing, testing, or integrating with PDC, use the
above production environments and ignore the below environments.

### Demo Environment

The demo environment is to demonstrate or showcase PDC capabilities using fake
or real data separately from the live production instance. It mimics the
production environment as closely as is practical otherwise. It authenticates
users via the production instance of Keycloak but has its own separate database
and S3 bucket. The demo environment is not intended for testing PDC code or
testing integrations with applications that use PDC.

- **API**: https://api.demo.philanthropydatacommons.org/
- **App (non-admin)**: https://app.demo.philanthropydatacommons.org/
- **Admin App**: https://admin.demo.philanthropydatacommons.org/

### Sandbox Environment

The sandbox environment is to test application integrations that use the PDC
API. It can use fake or real data separately from the live production and demo
instances. It mimics the production environment as closely as is practical
otherwise. It authenticates users via the production instance of Keycloak but
has its own separate database and S3 bucket. The sandbox environment is not
intended for demonstrating or showcasing PDC capabilities, nor for testing PDC
code in the PDC applications listed here as part of a delivery pipeline. It is
intended to be a production-like environment in which experiments can be safely
run using production code but without fear of disrupting production data.

- **API**: https://api.sandbox.philanthropydatacommons.org/
- **App (non-admin)**: https://app.sandbox.philanthropydatacommons.org/
- **Admin App**: https://admin.sandbox.philanthropydatacommons.org/

### Test Environment

The test environment is an internal environment used for testing of internal PDC
components' integration, such as Keycloak, the database, S3 buckets and/or their
respective configurations. It is used during stages of delivery to both the PDC
API and Keycloak (and in that sense could be called "staging"). Unlike the
above environments, it authenticates users via a test instance of Keycloak. It
mimics the production environment as closely as is practical otherwise and has
its own separate database and S3 bucket. The test environment is not intended
for demonstrating or showcasing PDC capabilities, nor for testing application
integrations that use the PDC API. The test environment can be expected to be in
a broken state at any given moment due to its use in development and testing.

- **API**: https://api.test.philanthropydatacommons.org/
- **App (non-admin)**: https://app.test.philanthropydatacommons.org/
- **Admin App**: https://admin.test.philanthropydatacommons.org/
- **Auth**: https://auth.test.philanthropydatacommons.org/realms/pdc/account

### Development Environments

Developers maintain development environments of applications on their own
development workstations. They may run their own Keycloak instances or use the
Keycloak production instance (or the Keycloak test instance when developing API
code).

### Preview Environments

Ephemeral preview environments for the purpose of testing unmerged changes in a
feature branch are not currently available but are aspirational.
