This file contains instructions for updating your Lightning-based Drupal site.

Lightning has a two-pronged update process. Out of the box, it provides a great
deal of default configuration for your site, but once it's installed, all that
configuration is "owned" by your site and Lightning cannot safely modify it
without potentially changing your site's behavior or, in a worst-case scenario,
causing data loss.

As it evolves, Lightning's default configuration may change. In certain limited
cases, Lightning will attempt to safely update configuration that it depends on
(which will usually be locked anyway to prevent you from modifying it).
Otherwise, Lightning will leave your configuration alone, respecting the fact
that your site owns it. So, to bring your site fully up-to-date with the latest
default configuration, you must follow the appropriate set(s) of instructions in
the "Version-specific updates" section of this file.

## Updating Lightning

**NEVER use ```drush pm-update``` to update Lightning!!** Lightning includes
specific, vetted, pre-tested versions of modules, and occasionally patches for
those modules (and Drupal core). ```drush pm-update``` will totally disregard
all of that and may break your site.

To update Lightning safely:

1. Download the latest version of Lightning from
   https://www.drupal.org/project/lightning and extract it.
2. In your Lightning site, delete the entire ```profiles/lightning``` directory.
3. Copy the ```profiles/lightning``` directory from your freshly downloaded
   version of Lightning into your site.
4. Visit ```update.php``` or run ```drush updb``` to perform any necessary
   database updates.
5. Perform any necessary manual version-specific updates (see below).

## Version-specific updates

These instructions describe how to update your site's configuration to bring
it in line with a newer version of Lightning. These changes are never made
automatically by Lightning because they have the potential to change the way
your site works.

Follow the instructions starting from the version of Lightning you currently
use. For example, if you are currently running Beta 1 and are trying to update
to Beta 3, you will need to follow the instructions for updating from Beta 1 to
Beta 2, then from Beta 2 to Beta 3, in that order.

### Beta 3 to Beta 4
Beta 4 is a Drupal Core update only release. There are no changes to Lightning.

### Beta 2 to Beta 3

* Scheduled updates to content are broken by Lightning's content moderation
  functionality. Beta 3 includes a workaround out-of-the-box which is NOT
  applied by the update. To implement the fix manually:
  * Go to *Configuration > Scheduled Updates Overview > Scheduled Update Types*
  * Edit the **Publish single node at certain time** update type
  * Under "Update Runner Settings", select **Latest Revision** from the
    "Update Runner" field
  * Under "Advanced Runner Options", select **The owner of the update.** from the
    "Run update as" field
  * Press Save

### Beta 1 to Beta 2

* Enable the ```view media``` permission for the ```anonymous``` and
  ```authenticated``` user roles.
* Install the Lightning Workflow module.
