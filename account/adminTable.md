## users_table
- 테이블명은 `users_table`이다.
- 컬럼의 구성은 id, username, password, name, avatar, remember_token, created_at, updaated_at으로 구성되어 있다.

### 설명
- 로그인 할 때 사용하는 계정 정보를 저장하는 테이블이다.

## roles_table
- 테이블명은 `roles_table`이다.
- 컬럼의 구성은 id, name, slug, created_at, updaated_at으로 구성되어 있다.

### 설명
- 계정의 권한을 설정하기 위한 테이블이다.
- slug는 유니크 속성을 가지고 있으며 네이밍 규칙은 `단어.단어`로 구성된다. 역할을 식별하기 위한 것이고 계층형으로 `범주A.범주A에 속하는 속성`과 같은 방식으로 식별자를 만들어 사용하면 된다.

## permissions_table
- 테이블명은 `permissions_table`이다.
- 컬럼의 구성은 id, name, slug, http_method, http_path, created_at, updaated_at으로 구성되어 있다.

### 설명
- 라라벨 어드민 경로로 리퀘스트를 보냈을 때 컨트롤러로 리퀘스트를 보낼 것인지 차단을 하고 419 에러를 응답할 것인지를 결정하는 테이블이다.
- 라라벨 어드민은 계정별로 주어지는 '기본 PATH'가 존재하며 라우터에 설정한 PATH를 통해 리퀘스트를 애플리케이션 내부(컨트롤러 또는 미들웨어)로 전달하기 위한 라우터 PATH가 존재한다. '도메인'+'기본 PATH'+'라우터 PATH'를 URL이 만들어지고 리퀘스트를 전달한다.
- 지정한 계정(user) 또는 역할(role)과 연결된 계정이 라우터 PATH로 리퀘스트를 전달할 때 리퀘스트를 애플리케이션 내부로 전달 할 수 있도록 허가할 라우터 경로를 추가하는 테이블이다.

## menu_table
- 테이블명은 `menu_table`이다.
- 컬럼의 구성은 id, parent_id, order, title, icon, uri, permission, created_at, updaated_at으로 구성되어 있다.

### 설명
- 라라벨 어드민의 레이아웃에는 사이드메뉴가 존재한다. 이 테이블에 지정한 메뉴를 이용해 역할별로 사이드 메뉴의 메뉴를 달리 할 수 있으며 표시할 메뉴와 메뉴를 눌렀을 때 접근할 uri를 설정한다.
- 사이드 메뉴에 표시할 대상만을 추가하며 특정 라우터 경로에 대한 접근에 대한 설정을 하지 않기 때문에 메뉴 설정과 메뉴를 표시할 역할을 설정하고 이와 함께 라우터 경로에 대한 접근을 허용 해 줘야 한다.

## role_users_table
- 테이블명은 `role_users_table`이다.
- 컬럼의 구성은 role_id, user_id, created_at, updaated_at으로 구성되어 있다.

### 설명
- `users_table`과 `roles_table` 테이블을 연결하기 위한 다대다 관계의 테이블이다.
- 하나의 유저가 여러 권한을 가질 수 있으며, 하나의 권한을 여러 유저가 가질 수도 있기 때문에 다대다 관계로 되어 있다.

## role_permissions_table
- 테이블명은 `role_permissions_table`이다.
- 컬럼의 구성은 role_id, permission_id, created_at, updaated_at으로 구성되어 있다.

### 설명
- `roles_table`과 `permissions_table` 테이블을 연결하기 위한 다대다 관계의 테이블이다.
- 하나의 역할은 여러 라우터 경로에 접근할 권한을 갖고, 각 라우터 경로는 여러 역할에 의해 사용되므로 다대다 관계를 갖는다.
- 로그인 계정이 특정 라우터 경로에 접근하기 위해서는 계정에 연결된 역할에 접근 가능한 라우터 경로를 연결하는 방법을 사용할 수 있다.

## user_permissions_table
- 테이블명은 `user_permissions_table`이다.
- 컬럼의 구성은 user_id, permission_id, created_at, updaated_at으로 구성되어 있다.

### 설명
- `user_table`과 `permissions_table` 테이블을 연결하기 위한 다대다 관계의 테이블이다.
- 하나의 계정은 여러 라우터 경로에 접근할 권한을 갖고, 각 라우터 경로는 여러 계정에 의해 사용되므로 다대다 관계를 갖는다.
- 로그인 계정이 특정 라우터 경로에 접근하기 위한 방법은 연결된 역할이 라우터 경로에 대한 접근 권한을 가지는 방법과 계정 자체에 라우터 경로에 대한 접근 권한을 부여하는 방법이 있다.

## role_menu_table
- 테이블명은 `role_menu_table`이다.
- 컬럼의 구성은 role_id, menu_id, created_at, updaated_at으로 구성되어 있다.

### 설명
- `role_table`과 `menu_table` 테이블을 연결하기 위한 다대다 관계의 테이블이다.
- 하나의 역할은 여러개의 표시할 메뉴를 가질 수 있고, 하나의 메뉴는 여러개의 역할에 할당되므로 다대다 관계를 갖는다.
- 메뉴는 계정에서 직접 연결되지 않고 역할과 직접 연결되므로 계정에서 메뉴의 접근을 하기 위해서는 계정이 가진 역할에 연결된 메뉴를 통해서 접근하도록 한다.

## operation_log_table
- 테이블명은 `operation_log_table`이다.
- 컬럼의 구성은 id, user_id, path, method, ip, input, user_id, created_at, updaated_at으로 구성되어 있다.

### 설명
- 로그인 계정의 로그인 이력을 기록한다.