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
  $config = array(
    'body'=>'',
    'total_fee' =>'',
    ...
  );
  Wxpay::instance('jsApi')->setConfig($config)->pay();
```

支付回调

```php
  $wxpay = Wxpay::instance('jsApi');
  $notify = $wxpay->verifyNotify(); //验证回调
  
  if($notify){
    //业务逻辑
    
    return 'success';
  }else{
    
    //业务逻辑
    
    
	return 'fail';
  }
  
```

