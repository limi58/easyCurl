# easyCurl
a light curl library  
一个把curl繁琐配置简单化的请求库

# Usage
## 实例化

```php
include './lib/easyCurl.php';
$EasyCurl = new EasyCurl();
```

## GET 请求

```php
$r = $EasyCurl->request(array(
    'url'=> 'http://dept9.guet.edu.cn/index.php/Ehym',
));
echo $r;
```

## POST 请求
```php
$r = $EasyCurl->request(array(
    'url'=> 'http://dept9.guet.edu.cn/index.php/Ehym',
    'data'=> 'uid=limi58&password=123456',
));
echo $r;
```

## 先获取 cookie 再请求
```php
// 存储 cookie
$EasyCurl->saveCookie(array(
    'url'=> 'http://www.baidu.com/doLogin',
    'dir'=> __DIR__.'./cookie',
    'data'=> 'uid=limi&password=123456',
));

// 用刚刚存储的 cookie 请求
$r = $EasyCurl->request(array(
    'url'=> 'http://www.baidu.com/admin',
    'cookie'=> true,
));

echo $r;
```

# API

## request($array) 发送请求

 有且仅有一个string参数时，此参数作为url参数GET  

 @param  string  $config['url']* // 必须。请求url  
 @param  string  $config['data'] // 发送post数据，默认为GET  
 @param  boolean $config['cookie'] = false // 是否发送cookie  
 @param  boolean $config['location'] = true // 是否自动重定向  
 @param  array   $config['headers'] = false // 带上header  
 @return string  


## saveCookie($array) 存cookie

 @param  $cookie['dir']* // 必须。cookie存目录  
 @param  $cookie['url']* // 必须。请求路径  
 @param  $cookie['data']* // 必须。请求数据  
 @return null  

# Support
http://www.imbgf.com 米不过分

    
