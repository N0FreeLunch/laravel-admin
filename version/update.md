## 컴포저로 버전업 명령어 실행하기
### 현재 버전 보기
```
composer show encore/laravel-admin
```

### 지정된 버전으로 업데이트
```
composer require encore/laravel-admin: 1.6.15 -vvv
```

### 참고
#### 최신 버전으로 업데이트
```
composer require encore/laravel-admin -vvv
```

#### 개발 버전으로 업데이트
```
composer require encore/laravel-admin:dev-master -vvv
```

## 스캐폴딩 변경 사항 적용
- 각 버전의 프론트앤드 리소스는 변경될 가능성이 있다.
```
/ / Force to publish release assets files
Php artisan vendor:publish --tag=laravel-admin-assets --force
// Force to publish release lang files
php artisan vendor:publish --tag=laravel-admin-lang --force
/ / Clean up the view cache
Php artisan view:clear
```
- 업데이트 후 브라우저 캐시를 정리하여 확인할 것.

## php 버전업

### php 7.4지원
#### 라라벨 어드민 라이브러리에서 7.4 사용시 버그 기록 확인
- https://github.com/z-song/laravel-admin/pull/4230/commits/2938fe4642291384eb4c7363c8a85e0520158428
- 7.4를 사용했을 때 버그 픽스가 생긴 라라벨 어드민 버전은 `v1.7.11`로 되어 있다. `v1.7.11`까지 버전을 올리고 7.4 버전으로 업데이트

## 라라벨 버전업
#### 라라벨 어드민 라이브러리에서 라라벨 8 대응
- https://github.com/z-song/laravel-admin/pull/5082

## 버전 별 변경사항 확인
- 버전 별 코드의 변경 사항을 코드 단위로 알 수 있다.

### 버전별 코드 비교 기능으로 들어감
- 깃 허브 사이드 메뉴의 다음 항목에서 `Releases` 부분을 클릭한다.
```
Releases 70
v1.8.19
Latest
on 24 May
```

### 버전 업그레이드
#### 1.6.10 -> 1.6.11
- https://github.com/z-song/laravel-admin/compare/v1.6.10...v1.6.11


## Reference
- https://laravel-admin.org/docs/en/updating
