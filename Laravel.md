# Laravel

## 创建控制器

### 普通控制器

`php artisan make:controller UserController`

### 基于 `RESTful` 的控制器

`php artisan make:controller PostController --resource`

### API 资源控制器

`php artisan make:controller API/PostController --api`

## 数据库操作

### 数据迁移

`php artisan make:migration create_users_table`
