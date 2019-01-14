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
