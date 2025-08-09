# Final Corrections to Apache Configuration for GLPI on AWS EC2 Debian

## Background
During the installation and setup of GLPI, a warning appeared indicating that the web server root directory configuration was not safe. This was because Apache allowed access to non-public files, which poses a security risk.

## Issues Identified
- The Apache configuration file `/etc/apache2/sites-available/000-default.conf` contained duplicate `<VirtualHost>` blocks.
- There was an unpaired closing `</Directory>` tag.
- The `<Directory>` directive for the GLPI folder `/var/www/html/glpi` was either misplaced or incorrectly structured.
- These issues could lead to insecure directory access and configuration errors.
Removed Unmatched Closing Tags.
Ensured all tags are properly opened and closed to avoid syntax errors.

Validation and Reload.

Ran sudo apache2ctl configtest to check the Apache configuration syntax.

Reloaded Apache with sudo systemctl reload apache2 to apply changes.

Why These Corrections Matter:
Ensuring only the GLPI directory is accessible reduces the risk of exposing sensitive files.

A clean and syntactically correct Apache configuration prevents server errors and potential downtime.

Proper permissions and overrides allow GLPI to function correctly with the required PHP modules and file access.

Next Steps:
Ask me credentials to test it
