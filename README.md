# GeoServer `jsonArrayContains` SQL Injection Patch

## About
This repository contains an emergency security patch authored by **UBITQUITY** for an unauthenticated SQL injection vulnerability discovered in GeoServer (August 2026). 

The vulnerability exists within the `jsonArrayContains` function when utilized alongside PostGIS and Oracle DataStores. Due to improper sanitization of user-supplied parameters, attackers could break out of the SQL query context and execute arbitrary SQL commands. On certain configurations (e.g., running with administrator privileges), this can lead to Remote Code Execution (RCE). 

This patch mitigates the vulnerability by applying the `escapeLiteral()` method to the evaluated string parameters before they are concatenated into the final SQL output, neutralizing the injection vector.

## Disclaimer
**SECURITY AND LIABILITY WARNING**
This patch is provided "AS-IS" without warranties or guarantees of any kind, either expressed or implied. 
*   This code is released for educational and defensive purposes to assist administrators in securing their infrastructure until an official upstream release is available.
*   Applying unofficial patches can have unintended side effects on your production environment. 
*   **UBITQUITY** and the authors of this patch assume no liability for any system instability, data loss, or security incidents resulting from the application or misuse of this code. 
*   Always test patches in a staging or development environment before deploying to production.

## How to Apply the Patch

You can apply this patch to your local GeoTools/GeoServer source code repository using standard command-line tools.

**Using Git:**
If you are inside a Git repository, run:
```bash
git apply geoserver-json-sqli-fix.patch
