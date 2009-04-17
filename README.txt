Block cache alter
------------------------
Requires Drupal 7

Author: Kristof De Jaeger - http://drupal.org/user/107403
Sponsored by One Agency - http://www.one-agency.be

Overview:
--------
Alter cache settings per block. Cache settings per block are now set in code,
but if you don't like the default - usually none - you can now easily change this
per block on the block configuration page in a fieldset called 'Caching settings'.
Install this to speed up block rendering for authenticated users.

Installation:
-------------
1. Place this module directory in your modules folder (this will
   usually be "sites/all/modules/").
2. Go to "administer -> build -> modules" and enable the module.

Configuration:
--------------
Go to "administer -> settings -> blockcache_alter" where you have 2 options

- Aggressive block caching: toggle this if you want block caching enabled even when
  modules are implementing the node_grants hook.
- Debug: apply this only during testing and development. It will show you
  messages when a block is refreshed.

Calling a block from code
-------------------------
Sometimes, developers do not enable the block itself, but call it with the 
module_invoke() function to put it somewhere they need. In that case blocks don't 
get cached even if all cache settings are set, because the block does not belong to 
any region. To work around that problem:

1. set the cache settings for the block as you desire, leave it disabled
2. call the block with the following piece of code:

<?php
$block = module_invoke('blockcache_alter', 'block', 'view', 'block,14');
print $block['content'];
?>

The last parameter should consist of the name of original block and its original delta 
seperated by comma. All blocks are cached that way.

Support:
--------
Please use the issue queue available at http://drupal.org/project/blockcache_alter to
file support and feature requests, bugs etc. Be as descriptive as you can.

Last updated:
------------
; $Id$
