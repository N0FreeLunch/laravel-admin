## CURD
- CURD는 create, update, read, delete를 의미한다.
- 웹의 MVC 모델에서 컨트롤러 구조의 컨트롤러 클래스의 메소드에 위치하여 라우터의 주소 형식에 따라 적절한 엑션을 동작시킨다.

## create
- 기본적으로 Form 객체의 동작은 주어진 모델의 데이터를 생성하는 동작을 한다.
- form 객체가 화면에 만들어 내는 input 태그를 통해서 전송하는 데이터를 전달 받을 때 디폴트 처리로는 모델의 데이터를 생성하는 역할을 한다.

## update
- 업대이트를 하기 위해서는 edit 메소드를 이용하여 모델에서 업데이트 할 대상의 아이디를 지정해 준다.
- insert 대신에 지정한 아이디의 레코드를 업데이트 하는 방식으로 동작을 하게 된다.
- `$form->edit($model->id)`

## delete
- 삭제를 하기 위해서는 destroy 메소드를 이용하여 모델에서 삭제할 대상의 아이디를 지정해 준다.
- 기본적으로 create와 update 동작이 함께 이뤄지기 때문에 이 동작을 차단하는 방법을 사용해 줘야 한다.
- `$form->destory($model->id)`

### 생성 변경 동작 차단
- 화면 폼에서 전송된 데이터의 생성 및 변경이 이뤄지기 전에 중간에 로직을 취소하고 다른 화면으로 리다이렉트 하는 코드를 만들어 준다.
- `redirect()->to` 뿐만 아니라 `back()`을 사용해서 송신 전 페이지를 다시 띄우는 방법 등을 사용해도 된다.
```php
// callback after form submission
$form->submitted(function (Form $form) {
    return redirect()->to('redirect/path');
});
```
```php
// callback before save
$form->saving(function (Form $form) {
    return redirect()->to('redirect/path');
});
```
- 저장이 되고 나서 동작하는 다음 콜백에서는 차단할 수 없다.
```text
// callback after save
$form->saved(function (Form $form) {
    //...
});
```
