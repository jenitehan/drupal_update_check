The Drupal Update Check Ansible role checks your sites for available updates and
notifies you when updates are available.

Leaving Update module enabled on live sites can lead to performance issues, but
leaving it disabled means you don't get emails about important security
updates.  This role goes out to your sites, checks for updates, and emails you if
security updates are available.

Drupal Configuration:

Enable the update module on your site and configure it with the email addresses to
notify about updates, and whether you want all updates or just security updates.
Disable the update module.

Ansible Configuration:

Add the role to the playbook of your choice.  The role uses a "check_sites" variable
to determine what sites to check.  That variable is a list of full paths to your Drupal
installs on the server (future plans include drush alias support).  For example:

check_sites:
  - /var/www/vhosts/example1.com/httpdocs/
  - /var/www/vhosts/example2.com/httpdocs/
  - /var/www/vhosts/example1.com/subdomains/foo/httpdocs/
  - /other/path/to/my/drupal/install/public_html/

Personally I set the variables in the group_vars directory of my playbook, in files for
each host.  Feel free to set that as you see fit.

Why use this?

I never leave update module enabled on live sites, but I get security update emails from
drupal.org when they are issued.  I can't remember what sites will have what modules
installed, so this provides a way for me to check which sites have security updates without
having to manually check each one, or leave update module enabled on a live site.

Requirements:

Drush needs to be installed on your server.