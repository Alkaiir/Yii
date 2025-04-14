
```
'language' => 'ru',
```

```
'request' => [
            // !!! insert a secret key in the following (if it is empty) - this is required by cookie validation
            'baseUrl' => '',
            'cookieValidationKey' => 'cookieValidationKey',
        ],
```

```
$config['modules']['debug'] = [
        'class' => 'yii\debug\Module',
        // uncomment the following to add your IP if you are not connecting from localhost.
        'allowedIPs' => ['127.0.0.1'],
    ];
```

```
$config['modules']['debug'] = [
        'class' => 'yii\debug\Module',
        // uncomment the following to add your IP if you are not connecting from localhost.
        'allowedIPs' => ['127.0.0.1'],
    ];
```

#User Model
```
public static function findIdentity($id)
    {
        return static::findOne($id);
    }

    public static function findIdentityByAccessToken($token, $type = null)
    {
        return null
    }

    public function getId()
    {
        return $this->id;
    }

    public function getAuthKey()
    {
        return null
    }

    public function validateAuthKey($authKey)
    {
        return false
    }

    public static function findByUsername($username)
    {
        return User::findOne(['username' => $username]);;
    }

    public function validatePassword($password)
    {
        return $this->password === md5($password);
    }
```
