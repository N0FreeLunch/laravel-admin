## 커스텀 유효성 검사 룰 등록

### 커스텀 벨리데이션 정의하기
```
use App\Rules\CustomRequired;

class CustomValidator extends \Illuminate\Validation\Validator {

    public function validateCustomRequired($attribute, $value, $parameters)
    {
        $this->setCustomMessages(['custom_required' => __('validation.required')]);
        
        return (new CustomRequired)->passes(attribute, value);
    }

}
```
- 사용하고자 할 유효성 검사의 규칙의 이름이 스네이크 케이스로 두고 이름 앞에 validate를 붙인 후 카멜케이스 형태로 메소드를 만든다.
- 위의 예에서는 유효성 검사 규칙을 `custom_required`로 사용할 수 있으며 이 유효성 검사 규칙을 정의할 때는 `validateCustomRequired`를 메소드로 써 준다.
- `$this->setCustomMessages(['custom_required' => __('validation.required')]);` setCustomMessages 메소드는 벨리데이션 메시지를 추가할 때 사용한다. `setCustomMessages` 메소드는 `\Illuminate\Validation\Validator`를 상속받은 `CustomValidator` 객체의 멤버에 배열 형식으로 벨리데이션 메시지를 저장한다. `custom_required` 유효성 

## 기본 유효성 검사 객체 덮어 쓰기
```
php artisan make:provider ValidateServiceProvider
```
- 프로바이더를 사용하여 라라벨 기본 유효성 검사 덮어 쓰기

```
namespace App\Providers;

use Illuminate\Support\Facades\View;
use Illuminate\Support\ServiceProvider;
use App\Validators\CustomValidator;

class ValidateServiceProvider extends ServiceProvider
{
    /**
     * Bootstrap any application services.
     *
     * @return void
     */
    public function boot()
    {
        Validator::resolver(function($translator, $data, $rules, $messages)
        {
            return new CustomValidator($translator, $data, $rules, $messages);
        });
    }
}
```

## 프로바이더 등록하기
-  `config/app.php` 설정파일에 위의 프로바이더를 등록 해 줘야 한다.
```
'providers' => [
    // Other Service Providers

    App\Providers\ComposerServiceProvider::class,
    App\Providers\ValidateServiceProvider::class,
],
```
- `'providers' => ` 함목에서 `App\Providers\ValidateServiceProvider::class`를 배열에 추가하여 프로바이더를 등록한다.