# Uyuni InSpec Profile

[![Build Status](https://travis-ci.org/stdevel/uyuni-inspec.svg?branch=master)](https://travis-ci.org/stdevel/uyuni-inspec)

This profile verifies an Uyuni installation.

Currently, only openSUSE 42.3 is supported - additional distributions will follow once Uyuni supports them.

# Checks
The following things are checked:
- Updated system
- Uyuni repository and required software packages
- Application ports (*80, 443, 5222, 5269, 4505, 4506, 5432*)
- Database deployment
- SUSE-related installation files
- Initial Uyuni organization and user

# Example
```
λ kitchen verify
Profile: InSpec Profile for Uyuni (uyuni)
...
  [PASS]  app-01: Web server running
     [PASS]  Port 80 should be listening
     [PASS]  Port 443 should be listening
  [PASS]  app-02: Jabber running
     [PASS]  Port 5222 should be listening
     [PASS]  Port 5269 should be listening
  [PASS]  app-03: Salt running
     [PASS]  Port 4505 should be listening
     [PASS]  Port 4506 should be listening
  [PASS]  app-04: PostgreSQL running
     [PASS]  Port 5432 should be listening
  [PASS]  app-05: Uyuni database deployed
     [PASS]  File /var/lib/pgsql/data/pg_hba.conf content should include "uyuni"
  [PASS]  app-06: Installation files
     [PASS]  File /root/uyuni_initial_setup.sh should not exist
     [PASS]  File /root/.MANAGER_SETUP_COMPLETE should exist
     [PASS]  File /root/.MANAGER_INITIALIZATION_COMPLETE should exist
  [PASS]  app-07: Initial content created
     [PASS]  uyuni users should include "vagrant"
     [PASS]  uyuni orgs should include "Vagrant"
  [PASS]  pkg-01: System up2date
     [PASS]  Command: `LANG=C zypper lu` stdout should include "No updates found"
  [PASS]  pkg-02: Uyuni repository exists
     [PASS]  Command: `LANG=C zypper lr` stdout should include "uyuni-server-stable"
  [PASS]  pkg-03: Uyuni packages installed
     [PASS]  System Package patterns-uyuni_server should be installed

Profile Summary: 10 successful controls, 0 control failures, 0 controls skipped
Test Summary: 16 successful, 0 failures, 0 skipped
```
