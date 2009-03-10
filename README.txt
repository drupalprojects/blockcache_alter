Block cache alter
------------------------
Requires Drupal 6

Author: Kristof De Jaeger - http://drupal.org/user/107403
Sponsored by One Agency - http://www.one-agency.be

Overview:
--------
Alter cache settings per block. Cache settings per block are now set in code,
but if you don't like the default - usually none, you can now easily change this
per block on the block configuration page in a fieldset called caching.
Install this to speed up block rendering for authenticated users.

The module also comes with 2 core patches you can apply to the block module
which will make block caching much smarter. You'll be able to set expire times
for block based on time and actions (nodeapi, comment and user).

1: blockcache_alter_with_node_grants.patch: most users should use this one.

2: blockcache_alter_no_node_grants.patch

Experienced users can use this one if one of your installed modules is implementing
a node_grants hook. Drupal checks on this and whenever 1 or more hooks are found
block caching is disabled completely. Handle with care though, this might
cause problems, be sure to test your site completely if you apply this patch.

Note: you can run this module *without* applying a patch, you simply don't get
that much options for refreshing a block.

Installation:
-------------
1. Place this module directory in your modules folder (this will
   usually be "sites/all/modules/").
2. Go to "administer -> build -> modules" and enable the module.

3. Apply one of the 2 core patches if you like. Copy them to the root 
   of your Drupal installation and run following command:
   
   patch -p0 < filename.
   
   To reverse the patch, simple run following command:
   
   patch -R -p0 < filename

Configuration:
--------------
Go to "administer -> settings -> blockcache_alter" where you have 2 options

- core patch: toggle this checkbox if you have applied one of the 2 core patches
  Additional options for refreshing the block will appear in the caching
  fieldset on the block configuration page. Note: if you didn't apply a core patch,
  these additional settings simplywon't have any effect.
- Debug: apply this only during testing and development. It will show you
  messages when a block is refreshed.
 
Support:
--------
Please use the issue queue available at http://drupal.org/project/imapulator to
file support and feature requests, bugs etc. Be as descriptive as you can.

Last updated:
------------
; $Id$
