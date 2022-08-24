## 커스텀 유효성 검사 규칙 객체 만들기
### 라라벨 아티산 커멘드로 유형성 검사 객체 만들기
```
php artisan make:rule CustomRequired
```

### 유효성 검사 규칙 객체 정의
```
namespace App\Rules;

use Illuminate\Contracts\Validation\Rule;
use Illuminate\Validation\Concerns\ValidatesAttributes;

class CustomRequired implements Rule
{
    use ValidatesAttributes;

    /**
     * Determine if the validation rule passes.
     *
     * @param  string  $attribute
     * @param  mixed  $value
     * @return bool
     */
    public function passes($attribute, $value)
    {
        return $this->validateRequired($attribute, $value);
    }

    /**
     * Get the validation error message.
     *
     * @return string
     */
    public function message()
    {
        return __('validation.required');
    }
}
```
- passes 메소드에는 유효성 검사 규칙을 설정한다. 유효성 검사를 통과하면 true를 반환하고 유효성 검사를 통과하지 않으면 false를 반환하는 식이다.
- message 메소드에는 유효성 검사를 통과하지 않았을 때, 표시할 메시지를 설정한다.

### 유효성 검사 객체 사용하기
```
$form->->rule([new CustomRequired])
```
- 배열 방식으로 유효성 검사 객체를 사용할 수 있다.