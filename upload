#!/usr/bin/php
<?php 
/**configuration**************************************************/
$localPath="/home/ms/workspace/r3";
$sshPath="/var/www/pearlfection.de/release02_schmitt";
$servers= array("perdix" , "patria");

/**configuration**************************************************/


$date = date('h-i-s, j-m-y');
$str="=======$date=========\n";

unset($argv[0]);
$file=getcwd().'/'.$argv[1];
$pattern=str_replace('/','\/',"^$localPath"); 

foreach($argv as $arg){
	$file=getcwd().'/'.$arg;

	if(preg_match("/^$pattern/", $file)){
		$switch='';
		if(is_dir($file)){
			$switch='-r';
		}


		$str.="=File $file =\n";
		$remoteFile = str_replace($localPath, $sshPath, $file);
		foreach($servers as $server){
			$cmd="scp $switch $file $server:$remoteFile";
			$str.="$cmd\n";
			exec($cmd);
		}
	} 

}
$log="/tmp/nautilusscp.cmp";
#file_put_contents($log, $str);
file_put_contents($log, $str,FILE_APPEND | LOCK_EX);
