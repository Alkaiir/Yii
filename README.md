
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

# User Model
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

```
public function beforeSave($insert)
    {
        $this->password = md5($this->password);
        return parent::beforeSave($insert);

    }
```

```
 public function rules()
    {
        return [
            [['full_name', 'phone', 'email', 'username', 'password'], 'required'],
            [['role'], 'string'],
            [['full_name', 'email', 'username'], 'string', 'max' => 100],
            [['phone'], 'string', 'max' => 20],
            [['password'], 'string', 'max' => 255, 'min' => 6],
            [['username'], 'unique'],
            ['role', 'default', 'value' => 'user'],
            ['email', 'email'],
            ['username', 'match', 'pattern' => '/^[A-z]\w*$/i'],
            ['full_name', 'match', 'pattern' => '/^[А-яЁё -]*$/u'],
            ['phone', 'match', 'pattern' => '/^\+?7\(\d{3}\)-\d{3}\-\d{2}\-\d{2}$/'],
        ];
    }
```

