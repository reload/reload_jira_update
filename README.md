# Create Jira issue for important project updates

Install this module and its dependencies and configure a Jira username
and password either at `admin/config/services/jira_rest` or better in
`settings.php` on the production server:

```php
$conf['jira_rest_username'] = 'marianne';
$conf['jira_rest_password'] = 'correcthorsebatterystaple';
```

Find the real credentials in [Meldium](https://launchpad.meldium.com/#/launchpad?edit=1ade21f3-88b8-4512-a371-53c0ec3e0840).

Install this as custom module on the site (it really is just a bunch
of configuration -- you are encourage to reconfigure the stuff
anyway).

Reconfigure the rule to create Jira issues in the appropriate project
for the site instead of the default which is `OUT`. You do that by
changing it here: https://github.com/reload/reload_jira_update/blob/7.x-1.x/reload_jira_update.rules_defaults.inc#L42

Whenever Drupal runs its project update check the module creates an
issue in Jira for newly discovered security updates, revoked modules,
and unsupported modules.

## Dependencies

The dependencies are (including indirect dependencies):

 * `ctools`
 * `entity`
 * `features`
 * `jira_rest`
 * `jira_rest_rules`
 * `rules`
 * `strongarm`
 * `ultimate_cron`
 * `update_rules`
   * Version 1.2 or [patched](https://www.drupal.org/files/issues/update_rules-release_link_for_recommended_release-2477835-4.patch) with [#2477835](https://www.drupal.org/node/2477835).
