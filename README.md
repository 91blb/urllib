# urllib

[![Build Status](https://secure.travis-ci.org/fengmk2/urllib.png)](http://travis-ci.org/fengmk2/urllib)

Help in opening URLs (mostly HTTP) in a complex world — basic and digest authentication, redirections, cookies and more. Like python  _urllib_ module.

## Install

    $ sudo npm install urllib

## Usage

### HTTP GET

    urllib.urlget('http://www.baidu.com/', {wd: 'cnodejs'}, function(err, data, res) {
        console.log(res.statusCode);
        console.log(res.headers);
        console.log(data.toString());
    });

http post juet use 'urlpost' replace 'urlget'

### Fetch HTTP headers only

    urllib.urlget('http://www.google.com/', null, {handle_data: false}, function(err, _, res) {
        console.log(res.statusCode);
        console.log(res.headers);
    };
    
### Don\'t handle 301 or 302 redirect
    
    urllib.urlget('http://www.google.com/', null, {handle_redirect: false}, function(err, data, res) {
        console.log(res.statusCode);
        console.log(res.headers);
    };
    
### Change User Agent header
    
    var chrome_agent = 'Mozilla/5.0 (Macintosh; Intel Mac OS X 10_6_7) AppleWebKit/534.30 (KHTML, like Gecko) Chrome/12.0.742.53 Safari/534.30';
    urllib.urlget('http://www.baidu.com/', 
            {wd: 'cnodejs'}, 
            {headers: {'user-agent': chrome_agent}}, 
            function(err, data, res) {
        console.log(res.statusCode);
        console.log(res.headers);
        console.log(data.toString());
    });