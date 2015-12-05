<?php

class EasyCurl{

    private $cookieFile;

    public function __construct(){

    }

    /**
     * request
     * @param  string  $config['url']*
     * @param  string  $config['data'] = false
     * @param  boolean $config['cookie'] = false
     * @param  boolean $config['location'] = true
     * @param  array   $config['headers'] = false
     * @return string
     */
    public function request($config){
        $ch = curl_init();

        // post data
        if($config['data']){
            curl_setopt($ch, CURLOPT_POST, 1);
            curl_setopt($ch, CURLOPT_POSTFIELDS, $config['data']);
        }

        // send cookie
        if($config['cookie']){
            curl_setopt($ch, CURLOPT_COOKIEFILE, $this->cookieFile);
        }

        // target address
        curl_setopt($ch, CURLOPT_URL, $config['url']);

        // header
        if (!$config['headers']) {
            $headers = array(
                "Content-type: text/xml;charset=utf-8",
                "Accept: text/html, application/xml;q=0.9, application/xhtml+xml, image/png, image/webp, image/jpeg, image/gif, image/x-xbitmap, */*;q=0.1",
                "Cache-Control: no-cache",
                "Pragma: no-cache",
                "User-Agent: Mozilla/5.0 (Windows NT 10.0; WOW64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/46.0.2490.80 Safari/537.36",
            );
            curl_setopt($ch, CURLOPT_HTTPHEADER, $headers);
        }else{
            curl_setopt($ch, CURLOPT_HTTPHEADER, $config['headers']);
        }
        
        // location
        curl_setopt($ch, CURLOPT_FOLLOWLOCATION, $config['location'] ? $config['location'] : 1);
        
        // exec
        $r = curl_exec($ch);
        curl_close($ch);
        return $r;

    }

    /**
     * saveCookie
     * @param  $cookie['dir']*
     * @param  $cookie['url']*
     * @param  $cookie['data']*
     * @return null
     */
    private function saveCookie($config){

        $cookieFile = tempnam($config['dir'], 'cookie');

        $this->cookieFile = $cookieFile; 

        $ch = curl_init();

        // save cookie
        curl_setopt($ch, CURLOPT_COOKIEJAR, $cookieFile);

        // target address
        curl_setopt($ch, CURLOPT_URL, $config['url']);

        // data
        curl_setopt($ch, CURLOPT_POST, 1);
        curl_setopt($ch, CURLOPT_POSTFIELDS, $config['data']);

        curl_exec($ch);
        curl_close($ch);

    }

}

?>
