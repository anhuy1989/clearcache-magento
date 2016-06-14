<?php
ini_set('display_errors',true);
$mageFilename = 'app/Mage.php';

require_once $mageFilename;

umask(0);
Mage::app('admin');

Mage::app()->cleanAllSessions();
Mage::app()->getCacheInstance()->flush();
Mage::app()->cleanCache();

$types = Array(
          0 => 'config', 
          1 => 'layout',
          2 => 'block_html', 
          3 => 'translate', 
          4 => 'collections',
          5 => 'eav',
          6 => 'config_api',
          7 => 'fullpage',
          8=>'config_api2'
        );

 $allTypes = Mage::app()->useCache();

$updatedTypes = 0;
foreach ($types as $code) {

    if (!empty($allTypes[$code])) {

        $allTypes[$code] = 0;
        $updatedTypes++;

    }
    $tags = Mage::app()->getCacheInstance()->cleanType($code);
}
if ($updatedTypes > 0) {
    Mage::app()->saveUseCache($allTypes);
    echo "Caches disabled Programmatically";
}
else {
    echo "Caches disabled Already";
}
