## Form 태그의 기본
- `use Encore\Admin\Form;` 모델을 불러서 laravel-admin의 Form 객체를 사용한다.
- Form 객체를 통해서 주어진 모델이 가지고 있는 레코드의 데이터를 생성하거나 변경할 수 있다.
- Form 객체를 통해서 주어진 모델의 데이터를 생성 및 변경하는 화면을 생성할 수 있다.

## 모델 할당하기
- 라라벨 엘로퀀트 모델을 `$form = new Form(Model);`형태로 할당한다.
