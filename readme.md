# wxpay
自用
WeiXin Payment 

###Install

1. 修改composer.json文件,加入```"jemoker/wxpay": "dev-master"```
```json
  "require": {
    "jemoker/wxpay": "dev-master"
  }
```

2. 修改app/config/app.php
```php
'providers' => array(
  		'Jemoker\Wxpay\WxpayServiceProvider'
)


'aliases' => array(
		'Wxpay' => 'Jemoker\Wxpay\Facades\WxpayFacade'
)
```

3. 运行```composer update ```命令
4. 运行```php artisan config:publish jemoker/wxpay```
5. 如有必要修改支付页面，运行```php artisan view:publish jemoker/wxpay```


###Usage

支付调用 
```php  
  $wxpay = app('wxpay');
  $params = array(
  	'body' => 'xxx',
  	'total_fee' => 'xxx',
  	'out_trade_no' => 'xxx',
  	'notify_url' => 'xxx',
  	'call_back_url' => 'xxx'
  );
  $wxpay->setParams($params);
```

支付回调

```php
  $wxpay = app('wxpay');
  $notify = $wxpay->verifyNotify(); 
  
  if($notify){
    //业务逻辑
    switch ($wxpay->data['result_code']) {
    	...
    }
    return 'success';
  }else{
    //业务逻辑
    return 'fail';
  }
```

