## config
- select 기능은 내부적으로 jquery의 select2 플러그인을 사용한다. select2 플러그인의 옵션을 사용할 수 있도록 지원하는 메소드가 `config`메소드이다.
```
    /**
     * Set config for select2.
     *
     * all configurations see https://select2.org/configuration/options-api
     *
     * @param string $key
     * @param mixed  $val
     *
     * @return $this
     */
    public function config($key, $val)
    {
        $this->config[$key] = $val;

        return $this;
    }
```
- [source code](https://github.com/z-song/laravel-admin/blob/27f535e824132229020cd4c6f261fa313fe09f85/src/Form/Field/Select.php#L367)
- [select2 document](https://select2.org/configuration/options-api)에서 option을 config 메소드의 첫 번째 인자로 지정할 값을 두 번째 인자로 전달한다.

## placeholder
- `select`폼은 `text`폼과 달리 내부적으로 동작 방식이 달라 placeholer 기능을 지원하지 않는다.
- select 기능은 내부적으로 jquery의 select2 플러그인을 사용하므로 select2 사용법을 laravel-admin의 select 기능으로 제공하는 config 메소드를 사용한다.
- placeholder 기능을 사용하기 위해서는 config 메소드를 활용하는 방법을 사용할 수 있다.
```php
$form->select('column_name','display_name')->config('placeholder', 'display placeholder message');
```

#### reference
- https://github.com/z-song/laravel-admin/issues/1111
