## Administrator
- [reference](https://github.com/z-song/laravel-admin/blob/master/src/Auth/Database/Administrator.php)
- `use Encore\Admin\Auth\Database\Administrator`으로 모델을 사용할 수 있다.
- 로그인 계정 정보를 담는 테이블을 매핑한 모델이다.

### Role 모델 연결
- 다대다 관계로 연결되어 있다. 중간 테이블은 `role_users_table`이다.

### Permission 모델 연결
- 다대다 관계로 연결되어 있다. 중간 테이블은 `user_permissions_table`이다.

- - -

## Menu
- [reference](https://github.com/z-song/laravel-admin/blob/master/src/Auth/Database/Menu.php)
- `use Encore\Admin\Auth\Database`으로 모델을 사용할 수 있다.
- 사이드 메뉴의 정보를 담는 테이블을 매핑한 모델이다.

### Role 모델 연결
- 다대다 관계로 연결되어 있다.
- `delete()` 메소드로 Role의 데이터를 삭제할 경우 다대다 중간 테이블인 `role_menu_table`에 연결된 데이터도 함께 삭제 된다.
- 대량 삭제를 하면서 중간 테이블의 데이터도 함께 삭제하기 위해서는 `detach()` 메소드를 사용한다. 이 경우 연결된 Role 모델의 데이터는 삭제되지 않는다.

- - -

## OperationLog
- [reference](https://github.com/z-song/laravel-admin/blob/master/src/Auth/Database/OperationLog.php)
- `use Encore\Admin\Auth\Database`으로 모델을 사용할 수 있다.
- 로그인 기록 정보를 담는 테이블을 매핑한 모델이다.

### Administrator 모델 연결
- Administrator와 OperationLog 모델은 일대다 연결이다.
- 로그인 기록 정보를 담는 테이블을 매핑한 모델이다.

- - -

## Permission
- [reference](https://github.com/z-song/laravel-admin/blob/master/src/Auth/Database/Permission.php)
- `use Encore\Admin\Auth\Database`으로 모델을 사용할 수 있다.
- 페이지 엑세스 권한 정보를 담은 테이블을 매핑한 모델이다.

### Role 모델 연결
- 다대다 관계로 연결되어 있다.
- `delete()` 메소드로 Role의 데이터를 삭제할 경우 다대다 중간 테이블인 `role_permissions_table`에 연결된 데이터도 함께 삭제 된다.
- 대량 삭제를 하면서 중간 테이블의 데이터도 함께 삭제하기 위해서는 `detach()` 메소드를 사용한다. 이 경우 연결된 Administrator 모델의 데이터는 삭제되지 않는다.

- - -

## Role
- [reference](https://github.com/z-song/laravel-admin/blob/master/src/Auth/Database/Role.php)
- `use Encore\Admin\Auth\Database`으로 모델을 사용할 수 있다.
- 계정의 여러 권한 집합인 역할 정보를 담는 테이블을 매핑한 모델이다.

### Administrator 모델 연결
- 다대다 관계로 연결되어 있다.
- `delete()` 메소드로 Role의 데이터를 삭제할 경우 다대다 중간 테이블인 `role_users_table`에 연결된 데이터도 함께 삭제 된다.
- 대량 삭제를 하면서 중간 테이블의 데이터도 함께 삭제하기 위해서는 `detach()` 메소드를 사용한다. 이 경우 연결된 Administrator 모델의 데이터는 삭제되지 않는다.

### Permissions 모델 연결
- 다대다 관계로 연결되어 있다.
- `delete()` 메소드로 Role의 데이터를 삭제할 경우 다대다 중간 테이블인 `role_permissions_table`에 연결된 데이터도 함께 삭제 된다.
- 대량 삭제를 하면서 중간 테이블의 데이터도 함께 삭제하기 위해서는 `detach()` 메소드를 사용한다. 이 경우 연결된 Permissions 모델의 데이터는 삭제되지 않는다.

### Menu 연결
- 모델과 다대다 관계로 연결되어 있다. 중간 테이블은 `role_menu_table`이다.
- 대량 삭제를 하면서 중간 테이블의 데이터도 함께 삭제하기 위해서는 `detach()` 메소드를 사용한다. 이 경우 연결된 Menu 모델의 데이터는 삭제되지 않는다.
