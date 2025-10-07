# API Documentation
This document provides an overview of the API routes for the [washing-cars project](https://abdelrhman-arfat.github.io/washing-cars/).

Base URLs:

# Authentication

- HTTP Authentication, scheme: bearer

# washing-cars

## GET Test if server is work !!

GET /test

> Response Examples

> 200 Response

```json
{
    "message": "string",
    "timestamp": "string"
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name        | Type   | Required | Restrictions | Title | description |
| ----------- | ------ | -------- | ------------ | ----- | ----------- |
| » message   | string | true     | none         |       | none        |
| » timestamp | string | true     | none         |       | none        |

# washing-cars/Authentication - تسجيل الدخول

## POST register - انشاء حساب

POST /auth/register

> Body Parameters

```yaml
phone: "0599999533"
name: abdo yasser
password: password
email: abdo@gmail.com
profile_image: file://C:\Users\COMPUMARTS\Downloads\logo2.png
```

### Params

| Name            | Location | Type           | Required | Description |
| --------------- | -------- | -------------- | -------- | ----------- |
| body            | body     | object         | no       | none        |
| » phone         | body     | string         | no       | none        |
| » name          | body     | string         | no       | none        |
| » password      | body     | string         | no       | none        |
| » email         | body     | string         | no       | none        |
| » profile_image | body     | string(binary) | no       | none        |

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "تم انشاء الحساب بنجاح",
    "data": null,
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name                 | Type    | Required | Restrictions | Title | description |
| -------------------- | ------- | -------- | ------------ | ----- | ----------- |
| » success            | boolean | true     | none         |       | none        |
| » message            | string  | true     | none         |       | none        |
| » data               | object  | true     | none         |       | none        |
| »» user              | object  | true     | none         |       | none        |
| »»» id               | integer | true     | none         |       | none        |
| »»» name             | string  | true     | none         |       | none        |
| »»» phone            | string  | true     | none         |       | none        |
| »»» email            | string  | true     | none         |       | none        |
| »»» role             | string  | true     | none         |       | none        |
| »»» wallet_balance   | string  | true     | none         |       | none        |
| »» token             | string  | true     | none         |       | none        |
| »» verification_code | string  | true     | none         |       | none        |
| »» token_type        | string  | true     | none         |       | none        |
| » errors             | null    | true     | none         |       | none        |

## POST login - تسجيل الدخول

POST /auth/login

> Body Parameters

```json
{
    "phone": "0599999533",
    "otp": "000000"
}
```

### Params

| Name | Location | Type   | Required | Description |
| ---- | -------- | ------ | -------- | ----------- |
| body | body     | object | no       | none        |

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "login success",
    "data": {
        "data": {
            "id": 5,
            "name": "abdo yasser",
            "phone": "0599999533",
            "email": "abdo@gmail.com",
            "is_phone_verified": true,
            "role": "customer",
            "wallet_balance": "0.00",
            "orders_count": 0,
            "total_spent": 0,
            "profile_image": "http://localhost:8000/uploads/users/profiles/17592156238922.png",
            "is_active": true,
            "last_login_at": "2025-09-30T07:04:33.000000Z",
            "created_at": "2025-09-30T07:00:24.000000Z",
            "updated_at": "2025-09-30T07:04:33.000000Z"
        },
        "token": "6|lHPcwJDhxpn4kwf4FjBY5EjhjXn3hjErV9q4vdTVe646b75f",
        "token_type": "Bearer"
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name                  | Type    | Required | Restrictions | Title | description |
| --------------------- | ------- | -------- | ------------ | ----- | ----------- |
| » success             | boolean | true     | none         |       | none        |
| » message             | string  | true     | none         |       | none        |
| » data                | object  | true     | none         |       | none        |
| »» data               | object  | true     | none         |       | none        |
| »»» id                | integer | true     | none         |       | none        |
| »»» name              | string  | true     | none         |       | none        |
| »»» phone             | string  | true     | none         |       | none        |
| »»» email             | string  | true     | none         |       | none        |
| »»» is_phone_verified | boolean | true     | none         |       | none        |
| »»» role              | string  | true     | none         |       | none        |
| »»» wallet_balance    | string  | true     | none         |       | none        |
| »»» orders_count      | integer | true     | none         |       | none        |
| »»» total_spent       | integer | true     | none         |       | none        |
| »»» profile_image     | string  | true     | none         |       | none        |
| »»» is_active         | boolean | true     | none         |       | none        |
| »»» last_login_at     | string  | true     | none         |       | none        |
| »»» created_at        | string  | true     | none         |       | none        |
| »»» updated_at        | string  | true     | none         |       | none        |
| »» token              | string  | true     | none         |       | none        |
| »» token_type         | string  | true     | none         |       | none        |
| »» user               | object  | true     | none         |       | none        |
| »»» id                | integer | true     | none         |       | none        |
| »»» name              | string  | true     | none         |       | none        |
| »»» phone             | string  | true     | none         |       | none        |
| »»» email             | string  | true     | none         |       | none        |
| »»» role              | string  | true     | none         |       | none        |
| »»» wallet_balance    | string  | true     | none         |       | none        |
| » errors              | null    | true     | none         |       | none        |

## POST logout - تسجيل الخروج

POST /user/logout

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

## POST login otp - OTP تسجيل الدخول

POST /auth/send-otp

> Body Parameters

```yaml
phone: "0599999533"
```

### Params

| Name    | Location | Type   | Required | Description |
| ------- | -------- | ------ | -------- | ----------- |
| body    | body     | object | no       | none        |
| » phone | body     | string | no       | none        |

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

## POST Send Rest Password Otp - ارسال

POST /auth/send-restpassword-otp

> Body Parameters

```yaml
phone: "0599999533"
```

### Params

| Name    | Location | Type   | Required | Description |
| ------- | -------- | ------ | -------- | ----------- |
| body    | body     | object | no       | none        |
| » phone | body     | string | no       | none        |

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

## POST Check is rest password otp is right - التحقق من otp

POST /auth/verify-restpassword-otp

> Body Parameters

```yaml
phone: "0599999533"
otp: "000000"
```

### Params

| Name    | Location | Type   | Required | Description |
| ------- | -------- | ------ | -------- | ----------- |
| body    | body     | object | no       | none        |
| » phone | body     | string | no       | none        |
| » otp   | body     | string | no       | none        |

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

## POST change password by otp - تغير البساورد otp

POST /auth/change-password-with-restpassword-otp

> Body Parameters

```yaml
phone: "0599999533"
otp: "000000"
password: "12345678"
```

### Params

| Name       | Location | Type   | Required | Description |
| ---------- | -------- | ------ | -------- | ----------- |
| body       | body     | object | no       | none        |
| » phone    | body     | string | no       | none        |
| » otp      | body     | string | no       | none        |
| » password | body     | string | no       | none        |

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

# washing-cars/user - المستخدم

## GET user data - بينات المستخدم

GET /user/profile

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "profile success",
    "data": {
        "user": {
            "id": 14,
            "name": "abdo yasser",
            "phone": "059999999",
            "email": "059999999@washingcars.com",
            "role": "customer",
            "wallet_balance": "0.00",
            "profile_image": null,
            "last_login_at": null
        }
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name               | Type    | Required | Restrictions | Title | description |
| ------------------ | ------- | -------- | ------------ | ----- | ----------- |
| » success          | boolean | true     | none         |       | none        |
| » message          | string  | true     | none         |       | none        |
| » data             | object  | true     | none         |       | none        |
| »» user            | object  | true     | none         |       | none        |
| »»» id             | integer | true     | none         |       | none        |
| »»» name           | string  | true     | none         |       | none        |
| »»» phone          | string  | true     | none         |       | none        |
| »»» email          | string  | true     | none         |       | none        |
| »»» role           | string  | true     | none         |       | none        |
| »»» wallet_balance | string  | true     | none         |       | none        |
| »»» profile_image  | null    | true     | none         |       | none        |
| »»» last_login_at  | null    | true     | none         |       | none        |
| » errors           | null    | true     | none         |       | none        |

## POST update user profile data - تحديث معلومات المستخدم

POST /user/profile

> Body Parameters

```yaml
name: new name
profile_image: file://C:\Users\COMPUMARTS\Downloads\logo2.png
_method: PUT
```

### Params

| Name            | Location | Type           | Required | Description |
| --------------- | -------- | -------------- | -------- | ----------- |
| body            | body     | object         | no       | none        |
| » name          | body     | string         | no       | none        |
| » profile_image | body     | string(binary) | no       | none        |
| » \_method      | body     | string         | no       | none        |

> Response Examples

> 401 Response

```json
{
    "success": true,
    "message": "update profile success",
    "data": {
        "data": {
            "id": 14,
            "name": "new name",
            "phone": "059999999",
            "email": "test@email.com",
            "role": "customer",
            "wallet_balance": "0.00",
            "profile_image": null,
            "last_login_at": "2025-08-24T10:33:21.000000Z"
        }
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                         | Description | Data schema |
| ---------------- | --------------------------------------------------------------- | ----------- | ----------- |
| 401              | [Unauthorized](https://tools.ietf.org/html/rfc7235#section-3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **401**

| Name               | Type    | Required | Restrictions | Title | description |
| ------------------ | ------- | -------- | ------------ | ----- | ----------- |
| » success          | boolean | true     | none         |       | none        |
| » message          | string  | true     | none         |       | none        |
| » data             | object  | true     | none         |       | none        |
| »» user            | object  | true     | none         |       | none        |
| »»» id             | integer | true     | none         |       | none        |
| »»» name           | string  | true     | none         |       | none        |
| »»» phone          | string  | true     | none         |       | none        |
| »»» email          | string  | true     | none         |       | none        |
| »»» role           | string  | true     | none         |       | none        |
| »»» wallet_balance | string  | true     | none         |       | none        |
| »»» profile_image  | null    | true     | none         |       | none        |
| »»» last_login_at  | string  | true     | none         |       | none        |
| » errors           | null    | true     | none         |       | none        |

## PUT change password - تغير الباسورد

PUT /user/change-password

> Body Parameters

```json
{
    "current_password": "password123",
    "password": "password"
}
```

### Params

| Name | Location | Type   | Required | Description |
| ---- | -------- | ------ | -------- | ----------- |
| body | body     | object | no       | none        |

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "change password success",
    "data": null,
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name      | Type    | Required | Restrictions | Title | description |
| --------- | ------- | -------- | ------------ | ----- | ----------- |
| » success | boolean | true     | none         |       | none        |
| » message | string  | true     | none         |       | none        |
| » data    | null    | true     | none         |       | none        |
| » errors  | null    | true     | none         |       | none        |

## POST refresh token - تحديث التوكن

POST /user/refresh

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "refresh token success",
    "data": {
        "token": "5|FBuoRzpabmRLlSzeO5k6EDqoTYjjwCCBLFMiV1EG62c3d019",
        "token_type": "Bearer"
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name          | Type    | Required | Restrictions | Title | description |
| ------------- | ------- | -------- | ------------ | ----- | ----------- |
| » success     | boolean | true     | none         |       | none        |
| » message     | string  | true     | none         |       | none        |
| » data        | object  | true     | none         |       | none        |
| »» token      | string  | true     | none         |       | none        |
| »» token_type | string  | true     | none         |       | none        |
| » errors      | null    | true     | none         |       | none        |

## POST resend otp code - اعادة ارسال ال otp

POST /user/resend-otp

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "resend otp success",
    "data": {
        "verification_code": "378440"
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name                 | Type    | Required | Restrictions | Title | description |
| -------------------- | ------- | -------- | ------------ | ----- | ----------- |
| » success            | boolean | true     | none         |       | none        |
| » message            | string  | true     | none         |       | none        |
| » data               | object  | true     | none         |       | none        |
| »» verification_code | string  | true     | none         |       | none        |
| » errors             | null    | true     | none         |       | none        |

## POST active user account - تفعيل حساب المستخدم

POST /user/verify-otp

> Body Parameters

```json
{
    "verification_code": "511951"
}
```

### Params

| Name | Location | Type   | Required | Description |
| ---- | -------- | ------ | -------- | ----------- |
| body | body     | object | no       | none        |

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

# washing-cars/cars - السيارات

## GET get all cars - جلب كل السيارات

GET /cars

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "string",
    "data": {
        "data": [null],
        "total": 0
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name      | Type    | Required | Restrictions | Title | description |
| --------- | ------- | -------- | ------------ | ----- | ----------- |
| » success | boolean | true     | none         |       | none        |
| » message | string  | true     | none         |       | none        |
| » data    | object  | true     | none         |       | none        |
| »» data   | [any]   | true     | none         |       | none        |
| »» total  | integer | true     | none         |       | none        |
| » errors  | null    | true     | none         |       | none        |

## POST create new car - اضافة سيارة جديده

POST /cars

> Body Parameters

```yaml
brand_id: "1"
type_id: "1"
plate_number: ABC-12
model_year: "2020"
color: Red
notes: string
is_default: "1"
"images[]":
    - file://C:\Users\COMPUMARTS\Downloads\ؤشق.jpeg
    - file://C:\Users\COMPUMARTS\Downloads\logo2.png
```

### Params

| Name           | Location | Type           | Required | Description |
| -------------- | -------- | -------------- | -------- | ----------- |
| body           | body     | object         | no       | none        |
| » brand_id     | body     | string         | no       | none        |
| » type_id      | body     | string         | no       | none        |
| » plate_number | body     | string         | no       | none        |
| » model_year   | body     | string         | no       | none        |
| » color        | body     | string         | no       | none        |
| » notes        | body     | string         | no       | none        |
| » is_default   | body     | boolean        | no       | none        |
| » images[]     | body     | string(binary) | no       | none        |

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "car created successfully",
    "data": {
        "data": {
            "brand_id": 1,
            "type_id": 1,
            "plate_number": "ABC-123",
            "model_year": 2020,
            "color": "Red",
            "notes": "string",
            "is_default": true,
            "user_id": 14,
            "updated_at": "2025-08-24T12:29:58.000000Z",
            "created_at": "2025-08-24T12:29:58.000000Z",
            "id": 58,
            "brand": {
                "id": 1,
                "name_ar": "تويوتا",
                "name_en": "Toyota",
                "logo_url": "http://localhost:8000/images/default-brand-logo.png",
                "is_active": true,
                "sort_order": 0,
                "created_at": "2025-08-14T12:20:44.000000Z",
                "updated_at": "2025-08-14T12:20:44.000000Z"
            },
            "type": {
                "id": 1,
                "name_ar": "سيارة صغيرة",
                "name_en": "Small Car",
                "description_ar": "سيارات صغيرة مثل تويوتا ياريس، هوندا سيتي",
                "description_en": "Small cars like Toyota Yaris, Honda City",
                "is_active": true,
                "sort_order": 1,
                "created_at": "2025-08-14T12:20:44.000000Z",
                "updated_at": "2025-08-14T12:20:44.000000Z"
            }
        }
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name                | Type    | Required | Restrictions | Title | description |
| ------------------- | ------- | -------- | ------------ | ----- | ----------- |
| » success           | boolean | true     | none         |       | none        |
| » message           | string  | true     | none         |       | none        |
| » data              | object  | true     | none         |       | none        |
| »» data             | object  | true     | none         |       | none        |
| »»» brand_id        | integer | true     | none         |       | none        |
| »»» type_id         | integer | true     | none         |       | none        |
| »»» plate_number    | string  | true     | none         |       | none        |
| »»» model_year      | integer | true     | none         |       | none        |
| »»» color           | string  | true     | none         |       | none        |
| »»» notes           | string  | true     | none         |       | none        |
| »»» is_default      | boolean | true     | none         |       | none        |
| »»» user_id         | integer | true     | none         |       | none        |
| »»» updated_at      | string  | true     | none         |       | none        |
| »»» created_at      | string  | true     | none         |       | none        |
| »»» id              | integer | true     | none         |       | none        |
| »»» brand           | object  | true     | none         |       | none        |
| »»»» id             | integer | true     | none         |       | none        |
| »»»» name_ar        | string  | true     | none         |       | none        |
| »»»» name_en        | string  | true     | none         |       | none        |
| »»»» logo_url       | string  | true     | none         |       | none        |
| »»»» is_active      | boolean | true     | none         |       | none        |
| »»»» sort_order     | integer | true     | none         |       | none        |
| »»»» created_at     | string  | true     | none         |       | none        |
| »»»» updated_at     | string  | true     | none         |       | none        |
| »»» type            | object  | true     | none         |       | none        |
| »»»» id             | integer | true     | none         |       | none        |
| »»»» name_ar        | string  | true     | none         |       | none        |
| »»»» name_en        | string  | true     | none         |       | none        |
| »»»» description_ar | string  | true     | none         |       | none        |
| »»»» description_en | string  | true     | none         |       | none        |
| »»»» is_active      | boolean | true     | none         |       | none        |
| »»»» sort_order     | integer | true     | none         |       | none        |
| »»»» created_at     | string  | true     | none         |       | none        |
| »»»» updated_at     | string  | true     | none         |       | none        |
| » errors            | null    | true     | none         |       | none        |

## GET get car by id - جلب معلومات السيارة

GET /cars/58

> Response Examples

> 404 Response

```json
{
    "success": true,
    "message": "string",
    "errors": null,
    "data": null
}
```

### Responses

| HTTP Status Code | Meaning                                                        | Description | Data schema |
| ---------------- | -------------------------------------------------------------- | ----------- | ----------- |
| 404              | [Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **404**

| Name      | Type    | Required | Restrictions | Title | description |
| --------- | ------- | -------- | ------------ | ----- | ----------- |
| » success | boolean | true     | none         |       | none        |
| » message | string  | true     | none         |       | none        |
| » errors  | null    | true     | none         |       | none        |
| » data    | null    | true     | none         |       | none        |

## PUT update car - تعديل السياره

PUT /cars/58

> Body Parameters

```json
"{\r\n    \"brand_id\": 1,\r\n    \"type_id\": 1,\r\n    \"plate_number\": \"ABC-123\",\r\n    \"model_year\": 2020,\r\n    \"color\": \"Blue\",\r\n    \"notes\": \"Updated notes\",\r\n}"
```

### Params

| Name | Location | Type   | Required | Description |
| ---- | -------- | ------ | -------- | ----------- |
| body | body     | object | no       | none        |

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "car updated successfully",
    "data": {
        "data": {
            "id": 58,
            "user_id": 14,
            "brand_id": 1,
            "type_id": 1,
            "plate_number": "abc-111",
            "model_year": "2020",
            "color": "Red",
            "notes": "string",
            "is_default": true,
            "brand": {
                "id": 1,
                "name_ar": "تويوتا",
                "name_en": "Toyota",
                "logo_url": "http://localhost:8000/images/default-brand-logo.png",
                "is_active": true,
                "sort_order": 0
            },
            "type": {
                "id": 1,
                "name_ar": "سيارة صغيرة",
                "name_en": "Small Car",
                "description_ar": "سيارات صغيرة مثل تويوتا ياريس، هوندا سيتي",
                "description_en": "Small cars like Toyota Yaris, Honda City",
                "is_active": true,
                "sort_order": 1
            }
        }
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name                | Type    | Required | Restrictions | Title | description |
| ------------------- | ------- | -------- | ------------ | ----- | ----------- |
| » success           | boolean | true     | none         |       | none        |
| » message           | string  | true     | none         |       | none        |
| » data              | object  | true     | none         |       | none        |
| »» data             | object  | true     | none         |       | none        |
| »»» id              | integer | true     | none         |       | none        |
| »»» user_id         | integer | true     | none         |       | none        |
| »»» brand_id        | integer | true     | none         |       | none        |
| »»» type_id         | integer | true     | none         |       | none        |
| »»» plate_number    | string  | true     | none         |       | none        |
| »»» model_year      | string  | true     | none         |       | none        |
| »»» color           | string  | true     | none         |       | none        |
| »»» notes           | string  | true     | none         |       | none        |
| »»» is_default      | boolean | true     | none         |       | none        |
| »»» brand           | object  | true     | none         |       | none        |
| »»»» id             | integer | true     | none         |       | none        |
| »»»» name_ar        | string  | true     | none         |       | none        |
| »»»» name_en        | string  | true     | none         |       | none        |
| »»»» logo_url       | string  | true     | none         |       | none        |
| »»»» is_active      | boolean | true     | none         |       | none        |
| »»»» sort_order     | integer | true     | none         |       | none        |
| »»» type            | object  | true     | none         |       | none        |
| »»»» id             | integer | true     | none         |       | none        |
| »»»» name_ar        | string  | true     | none         |       | none        |
| »»»» name_en        | string  | true     | none         |       | none        |
| »»»» description_ar | string  | true     | none         |       | none        |
| »»»» description_en | string  | true     | none         |       | none        |
| »»»» is_active      | boolean | true     | none         |       | none        |
| »»»» sort_order     | integer | true     | none         |       | none        |
| » errors            | null    | true     | none         |       | none        |

## DELETE delete car - حذف السياره

DELETE /cars/59

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

## PATCH set car to default car - جعل السياره اساسيه او افتراضيه

PATCH /cars/58/set-default

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "car set as default successfully",
    "data": {
        "data": {
            "id": 58,
            "user_id": 14,
            "brand_id": 1,
            "type_id": 1,
            "plate_number": "abc-111",
            "model_year": "2020",
            "color": "Red",
            "notes": "string",
            "is_default": true
        }
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name             | Type    | Required | Restrictions | Title | description |
| ---------------- | ------- | -------- | ------------ | ----- | ----------- |
| » success        | boolean | true     | none         |       | none        |
| » message        | string  | true     | none         |       | none        |
| » data           | object  | true     | none         |       | none        |
| »» data          | object  | true     | none         |       | none        |
| »»» id           | integer | true     | none         |       | none        |
| »»» user_id      | integer | true     | none         |       | none        |
| »»» brand_id     | integer | true     | none         |       | none        |
| »»» type_id      | integer | true     | none         |       | none        |
| »»» plate_number | string  | true     | none         |       | none        |
| »»» model_year   | string  | true     | none         |       | none        |
| »»» color        | string  | true     | none         |       | none        |
| »»» notes        | string  | true     | none         |       | none        |
| »»» is_default   | boolean | true     | none         |       | none        |
| » errors         | null    | true     | none         |       | none        |

# washing-cars/addresses - العنواين

## GET get users addresses - كل عنوانين المستخدم

GET /addresses

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "string",
    "data": {
        "data": [null],
        "total": 0
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name      | Type    | Required | Restrictions | Title | description |
| --------- | ------- | -------- | ------------ | ----- | ----------- |
| » success | boolean | true     | none         |       | none        |
| » message | string  | true     | none         |       | none        |
| » data    | object  | true     | none         |       | none        |
| »» data   | [any]   | true     | none         |       | none        |
| »» total  | integer | true     | none         |       | none        |
| » errors  | null    | true     | none         |       | none        |

## POST add new address - اضافة عنوان جديد للمستخدم

POST /addresses

> Body Parameters

```json
{
    "district_id": 1,
    "address_name": "المنزل",
    "full_address": "شارع الملك فهد، حي النزهة، الرياض",
    "building_number": "123",
    "street_name": "شارع الملك فهد",
    "neighborhood": "حي النزهة",
    "latitude": 24.7136,
    "longitude": 46.6753,
    "is_default": true,
    "additional_instructions": "بجانب مسجد النور"
}
```

### Params

| Name | Location | Type   | Required | Description |
| ---- | -------- | ------ | -------- | ----------- |
| body | body     | object | no       | none        |

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

## GET get address data - معلومات العنوان

GET /addresses/12

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "address retrieved successfully",
    "data": {
        "data": {
            "id": 12,
            "user_id": 12,
            "district_id": 1,
            "address_name": "المنزل",
            "full_address": "شارع الملك فهد، حي النزهة، الرياض",
            "building_number": "123",
            "street_name": "شارع الملك فهد",
            "neighborhood": "حي النزهة",
            "latitude": "24.71360000",
            "longitude": "46.67530000",
            "is_default": true,
            "additional_instructions": "بجانب مسجد النور",
            "created_at": "2025-08-25T06:22:49.000000Z",
            "updated_at": "2025-08-25T06:22:49.000000Z",
            "district": {
                "id": 1,
                "city_id": 1,
                "name_ar": "العليا",
                "name_en": "العليا",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z",
                "city": {
                    "id": 1,
                    "name_ar": "الرياض",
                    "name_en": "Riyadh",
                    "code": null,
                    "is_active": true,
                    "created_at": "2025-08-17T12:14:49.000000Z",
                    "updated_at": "2025-08-17T12:14:49.000000Z"
                }
            }
        }
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name                        | Type    | Required | Restrictions | Title | description |
| --------------------------- | ------- | -------- | ------------ | ----- | ----------- |
| » success                   | boolean | true     | none         |       | none        |
| » message                   | string  | true     | none         |       | none        |
| » data                      | object  | true     | none         |       | none        |
| »» data                     | object  | true     | none         |       | none        |
| »»» id                      | integer | true     | none         |       | none        |
| »»» user_id                 | integer | true     | none         |       | none        |
| »»» district_id             | integer | true     | none         |       | none        |
| »»» address_name            | string  | true     | none         |       | none        |
| »»» full_address            | string  | true     | none         |       | none        |
| »»» building_number         | string  | true     | none         |       | none        |
| »»» street_name             | string  | true     | none         |       | none        |
| »»» neighborhood            | string  | true     | none         |       | none        |
| »»» latitude                | string  | true     | none         |       | none        |
| »»» longitude               | string  | true     | none         |       | none        |
| »»» is_default              | boolean | true     | none         |       | none        |
| »»» additional_instructions | string  | true     | none         |       | none        |
| »»» created_at              | string  | true     | none         |       | none        |
| »»» updated_at              | string  | true     | none         |       | none        |
| »»» district                | object  | true     | none         |       | none        |
| »»»» id                     | integer | true     | none         |       | none        |
| »»»» city_id                | integer | true     | none         |       | none        |
| »»»» name_ar                | string  | true     | none         |       | none        |
| »»»» name_en                | string  | true     | none         |       | none        |
| »»»» code                   | null    | true     | none         |       | none        |
| »»»» description_ar         | null    | true     | none         |       | none        |
| »»»» description_en         | null    | true     | none         |       | none        |
| »»»» is_active              | boolean | true     | none         |       | none        |
| »»»» sort_order             | integer | true     | none         |       | none        |
| »»»» latitude               | null    | true     | none         |       | none        |
| »»»» longitude              | null    | true     | none         |       | none        |
| »»»» metadata               | null    | true     | none         |       | none        |
| »»»» created_at             | string  | true     | none         |       | none        |
| »»»» updated_at             | string  | true     | none         |       | none        |
| »»»» city                   | object  | true     | none         |       | none        |
| »»»»» id                    | integer | true     | none         |       | none        |
| »»»»» name_ar               | string  | true     | none         |       | none        |
| »»»»» name_en               | string  | true     | none         |       | none        |
| »»»»» code                  | null    | true     | none         |       | none        |
| »»»»» is_active             | boolean | true     | none         |       | none        |
| »»»»» created_at            | string  | true     | none         |       | none        |
| »»»»» updated_at            | string  | true     | none         |       | none        |
| » errors                    | null    | true     | none         |       | none        |

## PUT update address data - تحديث معلومات العنوان

PUT /addresses/12

> Body Parameters

```json
{
    "address_name": "العمل",
    "additional_instructions": "محدث"
}
```

### Params

| Name | Location | Type   | Required | Description |
| ---- | -------- | ------ | -------- | ----------- |
| body | body     | object | no       | none        |

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "address updated successfully",
    "data": {
        "data": {
            "id": 12,
            "user_id": 12,
            "district_id": 1,
            "address_name": "العمل",
            "full_address": "شارع الملك فهد، حي النزهة، الرياض",
            "building_number": "123",
            "street_name": "شارع الملك فهد",
            "neighborhood": "حي النزهة",
            "latitude": "24.71360000",
            "longitude": "46.67530000",
            "is_default": true,
            "additional_instructions": "محدث",
            "created_at": "2025-08-25T06:22:49.000000Z",
            "updated_at": "2025-08-25T06:24:37.000000Z",
            "district": {
                "id": 1,
                "city_id": 1,
                "name_ar": "العليا",
                "name_en": "العليا",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z",
                "city": {
                    "id": 1,
                    "name_ar": "الرياض",
                    "name_en": "Riyadh",
                    "code": null,
                    "is_active": true,
                    "created_at": "2025-08-17T12:14:49.000000Z",
                    "updated_at": "2025-08-17T12:14:49.000000Z"
                }
            }
        }
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name                        | Type    | Required | Restrictions | Title | description |
| --------------------------- | ------- | -------- | ------------ | ----- | ----------- |
| » success                   | boolean | true     | none         |       | none        |
| » message                   | string  | true     | none         |       | none        |
| » data                      | object  | true     | none         |       | none        |
| »» data                     | object  | true     | none         |       | none        |
| »»» id                      | integer | true     | none         |       | none        |
| »»» user_id                 | integer | true     | none         |       | none        |
| »»» district_id             | integer | true     | none         |       | none        |
| »»» address_name            | string  | true     | none         |       | none        |
| »»» full_address            | string  | true     | none         |       | none        |
| »»» building_number         | string  | true     | none         |       | none        |
| »»» street_name             | string  | true     | none         |       | none        |
| »»» neighborhood            | string  | true     | none         |       | none        |
| »»» latitude                | string  | true     | none         |       | none        |
| »»» longitude               | string  | true     | none         |       | none        |
| »»» is_default              | boolean | true     | none         |       | none        |
| »»» additional_instructions | string  | true     | none         |       | none        |
| »»» created_at              | string  | true     | none         |       | none        |
| »»» updated_at              | string  | true     | none         |       | none        |
| »»» district                | object  | true     | none         |       | none        |
| »»»» id                     | integer | true     | none         |       | none        |
| »»»» city_id                | integer | true     | none         |       | none        |
| »»»» name_ar                | string  | true     | none         |       | none        |
| »»»» name_en                | string  | true     | none         |       | none        |
| »»»» code                   | null    | true     | none         |       | none        |
| »»»» description_ar         | null    | true     | none         |       | none        |
| »»»» description_en         | null    | true     | none         |       | none        |
| »»»» is_active              | boolean | true     | none         |       | none        |
| »»»» sort_order             | integer | true     | none         |       | none        |
| »»»» latitude               | null    | true     | none         |       | none        |
| »»»» longitude              | null    | true     | none         |       | none        |
| »»»» metadata               | null    | true     | none         |       | none        |
| »»»» created_at             | string  | true     | none         |       | none        |
| »»»» updated_at             | string  | true     | none         |       | none        |
| »»»» city                   | object  | true     | none         |       | none        |
| »»»»» id                    | integer | true     | none         |       | none        |
| »»»»» name_ar               | string  | true     | none         |       | none        |
| »»»»» name_en               | string  | true     | none         |       | none        |
| »»»»» code                  | null    | true     | none         |       | none        |
| »»»»» is_active             | boolean | true     | none         |       | none        |
| »»»»» created_at            | string  | true     | none         |       | none        |
| »»»»» updated_at            | string  | true     | none         |       | none        |
| » errors                    | null    | true     | none         |       | none        |

## DELETE delete address - حذف العنوان

DELETE /addresses/12

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "address deleted successfully",
    "data": null,
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name      | Type    | Required | Restrictions | Title | description |
| --------- | ------- | -------- | ------------ | ----- | ----------- |
| » success | boolean | true     | none         |       | none        |
| » message | string  | true     | none         |       | none        |
| » data    | null    | true     | none         |       | none        |
| » errors  | null    | true     | none         |       | none        |

## PATCH set address to defual address - جعل العنوان هوا العموان الاساسي

PATCH /addresses/14/set-default

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

# washing-cars/order -الطلبات

## GET all user orders - كل طلبات النستخدم

GET /orders

### Params

| Name           | Location | Type   | Required | Description        |
| -------------- | -------- | ------ | -------- | ------------------ | --------- | --------- | --------- |
| status         | query    | string | no       | pending            | completed | confirmed | cancelled |
| per_page       | query    | string | no       | 1 < per_page < 100 |
| payment_status | query    | string | no       | pending            | paid      | failed    | refunded  |

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

## POST create new order - انشاء طلب جديد

POST /orders

> Body Parameters

```json
{
    "service_id": 1,
    "package_id": 3,
    "address_id": 1,
    "car_id": 6,
    "payment_method": "card",
    "booking_datetime": "2025-10-08",
    "from": "18:20",
    "to": "18:50",
    "addon_ids": [1, 2],
    "notes": "Please be careful with the paint"
}
```

### Params

| Name | Location | Type   | Required | Description |
| ---- | -------- | ------ | -------- | ----------- |
| body | body     | object | no       | none        |

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "تم حجز الطلب بنجاح",
    "data": {
        "id": 13,
        "order_number": "ORD-20251007-7D130A",
        "status": "pending",
        "payment_status": "pending",
        "total_price": 1040,
        "service_price": 1000,
        "addons_price": 40,
        "discount_amount": 0,
        "booking_datetime": "2025-10-08T00:00:00.000000Z",
        "start_time": "17:00",
        "end_time": "17:45",
        "payment_method": "card",
        "notes": "Please be careful with the paint",
        "delegate_notes": null,
        "cancellation_reason": null,
        "service": {
            "id": 1,
            "name": "غسيل خارجي",
            "price": 25,
            "duration_minutes": 30
        },
        "package": {
            "id": 3,
            "name": "الباقة الفصلية",
            "price": 1000
        },
        "car": {
            "id": 5,
            "plate_number": "ABC-1244",
            "model_year": "2020",
            "color": "Red"
        },
        "address": {
            "id": 1,
            "address_name": "المنزل",
            "full_address": "شارع الملك فهد، حي النزهة، الرياض"
        },
        "delegate": null,
        "addons": [
            {
                "id": 1,
                "name": "تلميع الشمع",
                "price": 15,
                "quantity": 1
            },
            {
                "id": 2,
                "name": "تنظيف المحرك",
                "price": 25,
                "quantity": 1
            }
        ],
        "rating": null,
        "transactions": [],
        "created_at": "2025-10-07T09:16:07.000000Z",
        "updated_at": "2025-10-07T09:16:07.000000Z"
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name                    | Type      | Required | Restrictions | Title | description |
| ----------------------- | --------- | -------- | ------------ | ----- | ----------- |
| » service_id            | integer   | true     | none         |       | none        |
| » package_id            | integer   | true     | none         |       | none        |
| » address_id            | integer   | true     | none         |       | none        |
| » car_id                | integer   | true     | none         |       | none        |
| » payment_method        | string    | true     | none         |       | none        |
| » booking_datetime      | string    | true     | none         |       | none        |
| » from                  | string    | true     | none         |       | none        |
| » to                    | string    | true     | none         |       | none        |
| » addon_ids             | [integer] | true     | none         |       | none        |
| » notes                 | string    | true     | none         |       | none        |
| » success               | boolean   | true     | none         |       | none        |
| » message               | string    | true     | none         |       | none        |
| » data                  | object    | true     | none         |       | none        |
| »» id                   | integer   | true     | none         |       | none        |
| »» order_number         | string    | true     | none         |       | none        |
| »» status               | string    | true     | none         |       | none        |
| »» payment_status       | string    | true     | none         |       | none        |
| »» total_price          | integer   | true     | none         |       | none        |
| »» service_price        | integer   | true     | none         |       | none        |
| »» addons_price         | integer   | true     | none         |       | none        |
| »» discount_amount      | integer   | true     | none         |       | none        |
| »» booking_datetime     | string    | true     | none         |       | none        |
| »» estimated_start_time | string    | true     | none         |       | none        |
| »» actual_start_time    | null      | true     | none         |       | none        |
| »» completed_at         | null      | true     | none         |       | none        |
| »» payment_method       | string    | true     | none         |       | none        |
| »» notes                | string    | true     | none         |       | none        |
| »» delegate_notes       | null      | true     | none         |       | none        |
| »» cancellation_reason  | null      | true     | none         |       | none        |
| »» service              | object    | true     | none         |       | none        |
| »»» id                  | integer   | true     | none         |       | none        |
| »»» name                | string    | true     | none         |       | none        |
| »»» price               | integer   | true     | none         |       | none        |
| »»» duration_minutes    | integer   | true     | none         |       | none        |
| »» package              | object    | true     | none         |       | none        |
| »»» id                  | integer   | true     | none         |       | none        |
| »»» name                | string    | true     | none         |       | none        |
| »»» price               | integer   | true     | none         |       | none        |
| »» car                  | object    | true     | none         |       | none        |
| »»» id                  | integer   | true     | none         |       | none        |
| »»» plate_number        | string    | true     | none         |       | none        |
| »»» model_year          | string    | true     | none         |       | none        |
| »»» color               | string    | true     | none         |       | none        |
| »» address              | object    | true     | none         |       | none        |
| »»» id                  | integer   | true     | none         |       | none        |
| »»» address_name        | string    | true     | none         |       | none        |
| »»» full_address        | string    | true     | none         |       | none        |
| »» delegate             | null      | true     | none         |       | none        |
| »» addons               | [object]  | true     | none         |       | none        |
| »»» id                  | integer   | true     | none         |       | none        |
| »»» name                | string    | true     | none         |       | none        |
| »»» price               | integer   | true     | none         |       | none        |
| »»» quantity            | integer   | true     | none         |       | none        |
| »» rating               | null      | true     | none         |       | none        |
| »» created_at           | string    | true     | none         |       | none        |
| »» updated_at           | string    | true     | none         |       | none        |
| » errors                | null      | true     | none         |       | none        |

## GET order data - معلومات ال order

GET /ordre/1

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

## PATCH cancel the order - الغاء الطلب

PATCH /orders/309/cancel

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

## PUT update the order - تدبث معولمات الطلب

PUT /orders/308

> Body Parameters

```json
{
    "notes": "Updated notes"
}
```

### Params

| Name | Location | Type   | Required | Description |
| ---- | -------- | ------ | -------- | ----------- |
| body | body     | object | no       | none        |

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "Order updated successfully",
    "data": {
        "id": 308,
        "order_number": "ORD-20250825-D85F5D",
        "status": "pending",
        "payment_status": "pending",
        "total_price": 167,
        "service_price": 135,
        "addons_price": 32,
        "discount_amount": 0,
        "booking_datetime": "2025-08-26T00:00:00.000000Z",
        "estimated_start_time": "2025-08-25T08:38:29.000000Z",
        "actual_start_time": null,
        "completed_at": null,
        "payment_method": "card",
        "notes": "Updated notes",
        "delegate_notes": null,
        "cancellation_reason": null,
        "service": {
            "id": 1,
            "name": "غسيل خارجي عادي",
            "price": 25,
            "duration_minutes": 30
        },
        "package": {
            "id": 3,
            "name": "الباقة الذهبية",
            "price": 135
        },
        "car": {
            "id": 8,
            "plate_number": "ABC-122",
            "model_year": "2020",
            "color": "Red"
        },
        "address": {
            "id": 13,
            "address_name": "المنزل",
            "full_address": "شارع الملك فهد، حي النزهة، الرياض"
        },
        "delegate": null,
        "addons": [
            {
                "id": 1,
                "name": "تنظيف عميق للسجاد",
                "price": 20,
                "quantity": 1
            },
            {
                "id": 2,
                "name": "تعطير فاخر",
                "price": 12,
                "quantity": 1
            }
        ],
        "rating": null,
        "created_at": "2025-08-25T08:08:29.000000Z",
        "updated_at": "2025-08-25T08:14:01.000000Z"
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name                    | Type     | Required | Restrictions | Title | description |
| ----------------------- | -------- | -------- | ------------ | ----- | ----------- |
| » success               | boolean  | true     | none         |       | none        |
| » message               | string   | true     | none         |       | none        |
| » data                  | object   | true     | none         |       | none        |
| »» id                   | integer  | true     | none         |       | none        |
| »» order_number         | string   | true     | none         |       | none        |
| »» status               | string   | true     | none         |       | none        |
| »» payment_status       | string   | true     | none         |       | none        |
| »» total_price          | integer  | true     | none         |       | none        |
| »» service_price        | integer  | true     | none         |       | none        |
| »» addons_price         | integer  | true     | none         |       | none        |
| »» discount_amount      | integer  | true     | none         |       | none        |
| »» booking_datetime     | string   | true     | none         |       | none        |
| »» estimated_start_time | string   | true     | none         |       | none        |
| »» actual_start_time    | null     | true     | none         |       | none        |
| »» completed_at         | null     | true     | none         |       | none        |
| »» payment_method       | string   | true     | none         |       | none        |
| »» notes                | string   | true     | none         |       | none        |
| »» delegate_notes       | null     | true     | none         |       | none        |
| »» cancellation_reason  | null     | true     | none         |       | none        |
| »» service              | object   | true     | none         |       | none        |
| »»» id                  | integer  | true     | none         |       | none        |
| »»» name                | string   | true     | none         |       | none        |
| »»» price               | integer  | true     | none         |       | none        |
| »»» duration_minutes    | integer  | true     | none         |       | none        |
| »» package              | object   | true     | none         |       | none        |
| »»» id                  | integer  | true     | none         |       | none        |
| »»» name                | string   | true     | none         |       | none        |
| »»» price               | integer  | true     | none         |       | none        |
| »» car                  | object   | true     | none         |       | none        |
| »»» id                  | integer  | true     | none         |       | none        |
| »»» plate_number        | string   | true     | none         |       | none        |
| »»» model_year          | string   | true     | none         |       | none        |
| »»» color               | string   | true     | none         |       | none        |
| »» address              | object   | true     | none         |       | none        |
| »»» id                  | integer  | true     | none         |       | none        |
| »»» address_name        | string   | true     | none         |       | none        |
| »»» full_address        | string   | true     | none         |       | none        |
| »» delegate             | null     | true     | none         |       | none        |
| »» addons               | [object] | true     | none         |       | none        |
| »»» id                  | integer  | true     | none         |       | none        |
| »»» name                | string   | true     | none         |       | none        |
| »»» price               | integer  | true     | none         |       | none        |
| »»» quantity            | integer  | true     | none         |       | none        |
| »» rating               | null     | true     | none         |       | none        |
| »» created_at           | string   | true     | none         |       | none        |
| »» updated_at           | string   | true     | none         |       | none        |
| » errors                | null     | true     | none         |       | none        |

## PATCH complete delegate order - اكمال طلب للمندوب

PATCH /orders/delegate/308/complete

> Response Examples

> 404 Response

```json
{
    "success": true,
    "message": "string",
    "errors": null,
    "data": null
}
```

### Responses

| HTTP Status Code | Meaning                                                        | Description | Data schema |
| ---------------- | -------------------------------------------------------------- | ----------- | ----------- |
| 404              | [Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **404**

| Name      | Type    | Required | Restrictions | Title | description |
| --------- | ------- | -------- | ------------ | ----- | ----------- |
| » success | boolean | true     | none         |       | none        |
| » message | string  | true     | none         |       | none        |
| » errors  | null    | true     | none         |       | none        |
| » data    | null    | true     | none         |       | none        |

# washing-cars/ratings - التقيمات

## GET all ratings - كل التقيماتت

GET /ratings

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

## POST add new rating - اضافة تقيم جديد

POST /ratings

> Body Parameters

```json
{
    "order_id": 1,
    "rating_score": 5,
    "service_quality": 5,
    "delegate_behavior": 5,
    "punctuality": 5,
    "comment": "nullable"
}
```

### Params

| Name | Location | Type   | Required | Description |
| ---- | -------- | ------ | -------- | ----------- |
| body | body     | object | no       | none        |

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

## GET get ratings data - معلومات التقيم

GET /ratings/1

> Response Examples

> 404 Response

```json
{
    "success": true,
    "message": "string",
    "errors": "string",
    "data": null
}
```

### Responses

| HTTP Status Code | Meaning                                                        | Description | Data schema |
| ---------------- | -------------------------------------------------------------- | ----------- | ----------- |
| 404              | [Not Found](https://tools.ietf.org/html/rfc7231#section-6.5.4) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **404**

| Name      | Type    | Required | Restrictions | Title | description |
| --------- | ------- | -------- | ------------ | ----- | ----------- |
| » success | boolean | true     | none         |       | none        |
| » message | string  | true     | none         |       | none        |
| » errors  | string  | true     | none         |       | none        |
| » data    | null    | true     | none         |       | none        |

## PUT update rating data - تحديث التقيم

PUT /ratings/1

> Body Parameters

```json
{
    "rating_score": 4,
    "service_quality": 5,
    "delegate_behavior": 4,
    "punctuality": 5,
    "comment": "Updated comment"
}
```

### Params

| Name | Location | Type   | Required | Description |
| ---- | -------- | ------ | -------- | ----------- |
| body | body     | object | no       | none        |

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "تم تحديث التقييم بنجاح",
    "data": {
        "data": {
            "id": 1,
            "order_id": 310,
            "user_id": 12,
            "delegate_id": 10,
            "rating_score": 4,
            "service_quality": 5,
            "delegate_behavior": 4,
            "punctuality": 5,
            "comment": "Updated comment",
            "is_verified": false,
            "is_helpful": false,
            "helpful_count": 0,
            "rating_details": null,
            "created_at": "2025-08-25T11:03:38.000000Z",
            "updated_at": "2025-08-25T11:15:25.000000Z"
        }
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name                  | Type    | Required | Restrictions | Title | description |
| --------------------- | ------- | -------- | ------------ | ----- | ----------- |
| » success             | boolean | true     | none         |       | none        |
| » message             | string  | true     | none         |       | none        |
| » data                | object  | true     | none         |       | none        |
| »» data               | object  | true     | none         |       | none        |
| »»» id                | integer | true     | none         |       | none        |
| »»» order_id          | integer | true     | none         |       | none        |
| »»» user_id           | integer | true     | none         |       | none        |
| »»» delegate_id       | integer | true     | none         |       | none        |
| »»» rating_score      | integer | true     | none         |       | none        |
| »»» service_quality   | integer | true     | none         |       | none        |
| »»» delegate_behavior | integer | true     | none         |       | none        |
| »»» punctuality       | integer | true     | none         |       | none        |
| »»» comment           | string  | true     | none         |       | none        |
| »»» is_verified       | boolean | true     | none         |       | none        |
| »»» is_helpful        | boolean | true     | none         |       | none        |
| »»» helpful_count     | integer | true     | none         |       | none        |
| »»» rating_details    | null    | true     | none         |       | none        |
| »»» created_at        | string  | true     | none         |       | none        |
| »»» updated_at        | string  | true     | none         |       | none        |
| » errors              | null    | true     | none         |       | none        |

## DELETE delete rating - حذف التقيم

DELETE /ratings/2

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "تم حذف التقييم بنجاح",
    "data": null,
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name      | Type    | Required | Restrictions | Title | description |
| --------- | ------- | -------- | ------------ | ----- | ----------- |
| » success | boolean | true     | none         |       | none        |
| » message | string  | true     | none         |       | none        |
| » data    | null    | true     | none         |       | none        |
| » errors  | null    | true     | none         |       | none        |

## PATCH make the rating is helpful - جعل التقيم مفيد

PATCH /ratings/3/helpful

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "تم تحديد التقييم كمفيد بنجاح",
    "data": {
        "helpful_count": 1,
        "is_helpful": true
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name             | Type    | Required | Restrictions | Title | description |
| ---------------- | ------- | -------- | ------------ | ----- | ----------- |
| » success        | boolean | true     | none         |       | none        |
| » message        | string  | true     | none         |       | none        |
| » data           | object  | true     | none         |       | none        |
| »» helpful_count | integer | true     | none         |       | none        |
| »» is_helpful    | boolean | true     | none         |       | none        |
| » errors         | null    | true     | none         |       | none        |

# washing-cars/Car Types and Brands - انوا السيارات و البرندات

## GET get all brands - كل البرندات

GET /brands

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "brands retrieved successfully",
    "data": {
        "data": [
            {
                "id": 14,
                "name_ar": "أكورا",
                "name_en": "Acura",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 11,
                "name_ar": "أودي",
                "name_en": "Audi",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 13,
                "name_ar": "إنفينيتي",
                "name_en": "Infiniti",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 21,
                "name_ar": "بورش",
                "name_en": "Porsche",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 9,
                "name_ar": "بي إم دبليو",
                "name_en": "BMW",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 1,
                "name_ar": "تويوتا",
                "name_en": "Toyota",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 19,
                "name_ar": "جاكوار",
                "name_en": "Jaguar",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 17,
                "name_ar": "جي إم سي",
                "name_en": "GMC",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 16,
                "name_ar": "جيب",
                "name_en": "Jeep",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 23,
                "name_ar": "سوبارو",
                "name_en": "Subaru",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 25,
                "name_ar": "سوزوكي",
                "name_en": "Suzuki",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 7,
                "name_ar": "شيفروليه",
                "name_en": "Chevrolet",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 8,
                "name_ar": "فورد",
                "name_en": "Ford",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 22,
                "name_ar": "فولفو",
                "name_en": "Volvo",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 15,
                "name_ar": "فولكس فاجن",
                "name_en": "Volkswagen",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 18,
                "name_ar": "كاديلاك",
                "name_en": "Cadillac",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 5,
                "name_ar": "كيا",
                "name_en": "Kia",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 20,
                "name_ar": "لاند روفر",
                "name_en": "Land Rover",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 12,
                "name_ar": "لكزس",
                "name_en": "Lexus",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 6,
                "name_ar": "مازدا",
                "name_en": "Mazda",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 10,
                "name_ar": "مرسيدس بنز",
                "name_en": "Mercedes-Benz",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 24,
                "name_ar": "ميتسوبيشي",
                "name_en": "Mitsubishi",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 3,
                "name_ar": "نيسان",
                "name_en": "Nissan",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 2,
                "name_ar": "هوندا",
                "name_en": "Honda",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            },
            {
                "id": 4,
                "name_ar": "هيونداي",
                "name_en": "Hyundai",
                "logo_url": "https://washing-cars.storage-te.com/images/default-brand-logo.png",
                "is_active": true
            }
        ]
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name          | Type     | Required | Restrictions | Title | description |
| ------------- | -------- | -------- | ------------ | ----- | ----------- |
| » success     | boolean  | true     | none         |       | none        |
| » message     | string   | true     | none         |       | none        |
| » data        | object   | true     | none         |       | none        |
| »» data       | [object] | true     | none         |       | none        |
| »»» id        | integer  | true     | none         |       | none        |
| »»» name_ar   | string   | true     | none         |       | none        |
| »»» name_en   | string   | true     | none         |       | none        |
| »»» logo_url  | string   | true     | none         |       | none        |
| »»» is_active | boolean  | true     | none         |       | none        |
| » errors      | null     | true     | none         |       | none        |

## GET Get all types - كل انواع السيارات

GET /types

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "types retrieved successfully",
    "data": {
        "data": [
            {
                "id": 4,
                "name_ar": "بيك أب",
                "name_en": "Pickup Truck",
                "description_ar": "شاحنة صغيرة مع حوض مفتوح لنقل البضائع",
                "description_en": "Light truck with open cargo bed",
                "is_active": true
            },
            {
                "id": 3,
                "name_ar": "دفع رباعي",
                "name_en": "SUV",
                "description_ar": "سيارة رياضية متعددة الاستخدامات ذات دفع رباعي",
                "description_en": "Sport Utility Vehicle with four-wheel drive capability",
                "is_active": true
            },
            {
                "id": 9,
                "name_ar": "ستيشن واجن",
                "name_en": "Station Wagon",
                "description_ar": "سيارة طويلة مع مساحة تخزين كبيرة",
                "description_en": "Extended car with large cargo space",
                "is_active": true
            },
            {
                "id": 1,
                "name_ar": "سيدان",
                "name_en": "Sedan",
                "description_ar": "سيارة ركاب بأربعة أبواب مع صندوق منفصل للأمتعة",
                "description_en": "Four-door passenger car with separate trunk compartment",
                "is_active": true
            },
            {
                "id": 6,
                "name_ar": "كروس أوفر",
                "name_en": "Crossover",
                "description_ar": "سيارة تجمع بين ميزات السيدان والدفع الرباعي",
                "description_en": "Vehicle combining sedan comfort with SUV versatility",
                "is_active": true
            },
            {
                "id": 5,
                "name_ar": "كوبيه",
                "name_en": "Coupe",
                "description_ar": "سيارة رياضية بباب أو بابين مع تصميم انسيابي",
                "description_en": "Sporty two-door car with sleek design",
                "is_active": true
            },
            {
                "id": 10,
                "name_ar": "كوبيه رياضي",
                "name_en": "Sports Coupe",
                "description_ar": "سيارة رياضية عالية الأداء بتصميم جذاب",
                "description_en": "High-performance sports car with attractive design",
                "is_active": true
            },
            {
                "id": 8,
                "name_ar": "كونفرتيبل",
                "name_en": "Convertible",
                "description_ar": "سيارة قابلة لطي السقف للاستمتاع بالهواء الطلق",
                "description_en": "Car with foldable roof for open-air driving",
                "is_active": true
            },
            {
                "id": 7,
                "name_ar": "ميني فان",
                "name_en": "Minivan",
                "description_ar": "سيارة عائلية كبيرة تتسع لعدد كبير من الركاب",
                "description_en": "Large family vehicle designed for passenger capacity",
                "is_active": true
            },
            {
                "id": 2,
                "name_ar": "هاتشباك",
                "name_en": "Hatchback",
                "description_ar": "سيارة صغيرة مدمجة مع باب خلفي منحني",
                "description_en": "Compact car with rear door that swings upward",
                "is_active": true
            }
        ]
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name               | Type     | Required | Restrictions | Title | description |
| ------------------ | -------- | -------- | ------------ | ----- | ----------- |
| » success          | boolean  | true     | none         |       | none        |
| » message          | string   | true     | none         |       | none        |
| » data             | object   | true     | none         |       | none        |
| »» data            | [object] | true     | none         |       | none        |
| »»» id             | integer  | true     | none         |       | none        |
| »»» name_ar        | string   | true     | none         |       | none        |
| »»» name_en        | string   | true     | none         |       | none        |
| »»» description_ar | string   | true     | none         |       | none        |
| »»» description_en | string   | true     | none         |       | none        |
| »»» is_active      | boolean  | true     | none         |       | none        |
| » errors           | null     | true     | none         |       | none        |

# washing-cars/Settings - الاعدادات

## GET get pup faq - الاسىله الشائعه

GET /faq

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "السؤال الشائع retrieved successfully",
    "data": {
        "data": [
            {
                "id": 1,
                "question_ar": "ما هي مدة الخدمة  ؟",
                "question_en": "What is the service duration?",
                "answer_ar": "تختلف مدة الخدمة حسب نوع الخدمة المطلوبة، وتتراوح بين 30 دقيقة إلى ساعتين.تختلف مدة الخدمة حسب نوع الخدمة المطلوبة، وتتراوح بين 30 دقيقة إلى ساعتين.",
                "answer_en": "The service duration varies depending on the type of service requested, ranging from 30 minutes to 2 hours.The service duration varies depending on the type of service requested, ranging from 30 minutes to 2 hours.",
                "image": null,
                "created_at": "2025-09-30T09:34:52.000000Z",
                "updated_at": "2025-09-30T10:25:37.000000Z"
            },
            {
                "id": 2,
                "question_ar": "aadsfasdf",
                "question_en": "asdfasdfasd",
                "answer_ar": "fThe service duration varies depending on the type of service requested, ranging from 30 minutes to 2 hours.The service duration varies depending on the type of service requested, ranging from 30 minutes to 2 hours.",
                "answer_en": "The service duration varies depending on the type of service requested, ranging from 30 minutes to 2 hours.The service duration varies depending on the type of service requested, ranging from 30 minutes to 2 hours.",
                "image": null,
                "created_at": "2025-09-30T10:25:49.000000Z",
                "updated_at": "2025-09-30T10:25:49.000000Z"
            },
            {
                "id": 3,
                "question_ar": "ما هي مدة الخدمة؟",
                "question_en": "What is the service duration?",
                "answer_ar": "تختلف مدة الخدمة حسب نوع الخدمة المطلوبة، وتتراوح بين 30 دقيقة إلى ساعتين.",
                "answer_en": "The service duration varies depending on the type of service requested, ranging from 30 minutes to 2 hours.",
                "image": null,
                "created_at": "2025-09-30T10:27:27.000000Z",
                "updated_at": "2025-09-30T10:27:27.000000Z"
            }
        ],
        "total": 3
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name            | Type     | Required | Restrictions | Title | description |
| --------------- | -------- | -------- | ------------ | ----- | ----------- |
| » success       | boolean  | true     | none         |       | none        |
| » message       | string   | true     | none         |       | none        |
| » data          | object   | true     | none         |       | none        |
| »» data         | [object] | true     | none         |       | none        |
| »»» id          | integer  | true     | none         |       | none        |
| »»» question_ar | string   | true     | none         |       | none        |
| »»» question_en | string   | true     | none         |       | none        |
| »»» answer_ar   | string   | true     | none         |       | none        |
| »»» answer_en   | string   | true     | none         |       | none        |
| »»» image       | null     | true     | none         |       | none        |
| »»» created_at  | string   | true     | none         |       | none        |
| »»» updated_at  | string   | true     | none         |       | none        |
| »» total        | integer  | true     | none         |       | none        |
| » errors        | null     | true     | none         |       | none        |

## GET about us - عن الشركه

GET /about-us

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "من نحن ",
    "data": {
        "data": [
            {
                "id": 1,
                "title_ar": "من نحن",
                "title_en": "About Us",
                "description_ar": "نحن شركة متخصصة في خدمات غسيل السيارات بأعلى معايير الجودة والاحترافية.نحن شركة متخصصة في خدمات غسيل السيارات بأعلى معايير الجودة والاحترافية.نحن شركة متخصصة في خدمات غسيل السيارات بأعلى معايير الجودة والاحترافية.نحن شركة متخصصة في خدمات غسيل السيارات بأعلى معايير الجودة والاحترافية.نحن شركة متخصصة في خدمات غسيل السيارات بأعلى معايير الجودة والاحترافية.",
                "description_en": "We are a specialized company in car washing services with the highest quality and professionalism standards.We are a specialized company in car washing services with the highest quality and professionalism standards.We are a specialized company in car washing services with the highest quality and professionalism standards.\r\n\r\nWe are a specialized company in car washing services with the highest quality and professionalism standards.",
                "image": null,
                "created_at": "2025-09-30T09:35:02.000000Z",
                "updated_at": "2025-09-30T09:37:53.000000Z"
            }
        ],
        "total": 1
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name               | Type     | Required | Restrictions | Title | description |
| ------------------ | -------- | -------- | ------------ | ----- | ----------- |
| » success          | boolean  | true     | none         |       | none        |
| » message          | string   | true     | none         |       | none        |
| » data             | object   | true     | none         |       | none        |
| »» data            | [object] | true     | none         |       | none        |
| »»» id             | integer  | false    | none         |       | none        |
| »»» title_ar       | string   | false    | none         |       | none        |
| »»» title_en       | string   | false    | none         |       | none        |
| »»» description_ar | string   | false    | none         |       | none        |
| »»» description_en | string   | false    | none         |       | none        |
| »»» image          | null     | false    | none         |       | none        |
| »»» created_at     | string   | false    | none         |       | none        |
| »»» updated_at     | string   | false    | none         |       | none        |
| »» total           | integer  | true     | none         |       | none        |
| » errors           | null     | true     | none         |       | none        |

## GET contact data - معلومات التواصل

GET /contact-us

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "string",
    "data": {
        "data": [
            {
                "id": 0,
                "name": "string",
                "email": "string",
                "phone": "string",
                "address": "string",
                "message": "string",
                "social_media": {
                    "tiktok": "string",
                    "twitter": "string",
                    "youtube": "string",
                    "facebook": "string",
                    "linkedin": "string",
                    "snapchat": "string",
                    "telegram": "string",
                    "whatsapp": "string",
                    "instagram": "string",
                    "pinterest": "string"
                },
                "created_at": "string"
            }
        ],
        "total": 0
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name             | Type     | Required | Restrictions | Title | description |
| ---------------- | -------- | -------- | ------------ | ----- | ----------- |
| » success        | boolean  | true     | none         |       | none        |
| » message        | string   | true     | none         |       | none        |
| » data           | object   | true     | none         |       | none        |
| »» data          | [object] | true     | none         |       | none        |
| »»» id           | integer  | false    | none         |       | none        |
| »»» name         | string   | false    | none         |       | none        |
| »»» email        | string   | false    | none         |       | none        |
| »»» phone        | string   | false    | none         |       | none        |
| »»» address      | string   | false    | none         |       | none        |
| »»» message      | string   | false    | none         |       | none        |
| »»» social_media | object   | false    | none         |       | none        |
| »»»» tiktok      | string   | true     | none         |       | none        |
| »»»» twitter     | string   | true     | none         |       | none        |
| »»»» youtube     | string   | true     | none         |       | none        |
| »»»» facebook    | string   | true     | none         |       | none        |
| »»»» linkedin    | string   | true     | none         |       | none        |
| »»»» snapchat    | string   | true     | none         |       | none        |
| »»»» telegram    | string   | true     | none         |       | none        |
| »»»» whatsapp    | string   | true     | none         |       | none        |
| »»»» instagram   | string   | true     | none         |       | none        |
| »»»» pinterest   | string   | true     | none         |       | none        |
| »»» created_at   | string   | false    | none         |       | none        |
| »» total         | integer  | true     | none         |       | none        |
| » errors         | null     | true     | none         |       | none        |

## GET privacy and policy - سياية الخصويه

GET /privacy-policy

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "سياسة الخصوصية ",
    "data": {
        "data": [
            {
                "id": 2,
                "title_ar": "صقسبيل",
                "title_en": "سيبل",
                "description_ar": "صقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيل",
                "description_en": "صقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيلصقسبيل",
                "image": null,
                "created_at": "2025-09-30T10:23:33.000000Z",
                "updated_at": "2025-09-30T10:23:56.000000Z"
            }
        ],
        "total": 1
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name               | Type     | Required | Restrictions | Title | description |
| ------------------ | -------- | -------- | ------------ | ----- | ----------- |
| » success          | boolean  | true     | none         |       | none        |
| » message          | string   | true     | none         |       | none        |
| » data             | object   | true     | none         |       | none        |
| »» data            | [object] | true     | none         |       | none        |
| »»» id             | integer  | false    | none         |       | none        |
| »»» title_ar       | string   | false    | none         |       | none        |
| »»» title_en       | string   | false    | none         |       | none        |
| »»» description_ar | string   | false    | none         |       | none        |
| »»» description_en | string   | false    | none         |       | none        |
| »»» image          | null     | false    | none         |       | none        |
| »»» created_at     | string   | false    | none         |       | none        |
| »»» updated_at     | string   | false    | none         |       | none        |
| »» total           | integer  | true     | none         |       | none        |
| » errors           | null     | true     | none         |       | none        |

# washing-cars/services - الخدمات

## GET get all services - كل الخدمات

GET /services

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

## GET all adon service - كل الخدمات الاضافيه

GET /services/addon-services

> Response Examples

> 200 Response

```json
{}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

## POST get times of the service - اوقات الخدمه

POST /services/time-to-order

> Body Parameters

```json
{
    "service_id": 1,
    "booking_datetime": "2025-10-08",
    "car_id": 6
}
```

### Params

| Name | Location | Type   | Required | Description |
| ---- | -------- | ------ | -------- | ----------- |
| body | body     | object | no       | none        |

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "تم استرجاع الوقت بنجاح",
    "data": [
        {
            "from": "08:00",
            "to": "08:45",
            "label": "من 8:00 صباحاً إلى 8:45 صباحاً"
        },
        {
            "from": "08:45",
            "to": "09:30",
            "label": "من 8:45 صباحاً إلى 9:30 صباحاً"
        },
        {
            "from": "09:30",
            "to": "10:15",
            "label": "من 9:30 صباحاً إلى 10:15 صباحاً"
        },
        {
            "from": "10:15",
            "to": "11:00",
            "label": "من 10:15 صباحاً إلى 11:00 صباحاً"
        },
        {
            "from": "11:00",
            "to": "11:45",
            "label": "من 11:00 صباحاً إلى 11:45 صباحاً"
        },
        {
            "from": "11:45",
            "to": "12:30",
            "label": "من 11:45 صباحاً إلى 12:30 مساءً"
        },
        {
            "from": "12:30",
            "to": "13:15",
            "label": "من 12:30 مساءً إلى 1:15 مساءً"
        },
        {
            "from": "13:15",
            "to": "14:00",
            "label": "من 1:15 مساءً إلى 2:00 مساءً"
        },
        {
            "from": "14:00",
            "to": "14:45",
            "label": "من 2:00 مساءً إلى 2:45 مساءً"
        },
        {
            "from": "14:45",
            "to": "15:30",
            "label": "من 2:45 مساءً إلى 3:30 مساءً"
        },
        {
            "from": "15:30",
            "to": "16:15",
            "label": "من 3:30 مساءً إلى 4:15 مساءً"
        },
        {
            "from": "16:15",
            "to": "17:00",
            "label": "من 4:15 مساءً إلى 5:00 مساءً"
        },
        {
            "from": "17:00",
            "to": "17:45",
            "label": "من 5:00 مساءً إلى 5:45 مساءً"
        },
        {
            "from": "17:45",
            "to": "18:30",
            "label": "من 5:45 مساءً إلى 6:30 مساءً"
        },
        {
            "from": "18:30",
            "to": "19:15",
            "label": "من 6:30 مساءً إلى 7:15 مساءً"
        },
        {
            "from": "19:15",
            "to": "20:00",
            "label": "من 7:15 مساءً إلى 8:00 مساءً"
        },
        {
            "from": "20:00",
            "to": "20:45",
            "label": "من 8:00 مساءً إلى 8:45 مساءً"
        },
        {
            "from": "20:45",
            "to": "21:30",
            "label": "من 8:45 مساءً إلى 9:30 مساءً"
        }
    ],
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name                                | Type     | Required | Restrictions | Title | description |
| ----------------------------------- | -------- | -------- | ------------ | ----- | ----------- |
| » success                           | boolean  | true     | none         |       | none        |
| » message                           | string   | true     | none         |       | none        |
| » data                              | [object] | true     | none         |       | none        |
| »» from                             | string   | true     | none         |       | none        |
| »» to                               | string   | true     | none         |       | none        |
| »» label                            | string   | true     | none         |       | none        |
| »» من 8:00 صباحاً إلى 8:45 صباحاً   | object   | false    | none         |       | none        |
| »»» from                            | string   | true     | none         |       | none        |
| »»» to                              | string   | true     | none         |       | none        |
| »» من 8:45 صباحاً إلى 9:30 صباحاً   | object   | false    | none         |       | none        |
| »»» from                            | string   | true     | none         |       | none        |
| »»» to                              | string   | true     | none         |       | none        |
| »» من 9:30 صباحاً إلى 10:15 صباحاً  | object   | false    | none         |       | none        |
| »»» from                            | string   | true     | none         |       | none        |
| »»» to                              | string   | true     | none         |       | none        |
| »» من 10:15 صباحاً إلى 11:00 صباحاً | object   | false    | none         |       | none        |
| »»» from                            | string   | true     | none         |       | none        |
| »»» to                              | string   | true     | none         |       | none        |
| »» من 11:00 صباحاً إلى 11:45 صباحاً | object   | false    | none         |       | none        |
| »»» from                            | string   | true     | none         |       | none        |
| »»» to                              | string   | true     | none         |       | none        |
| »» من 11:45 صباحاً إلى 12:30 مساءً  | object   | false    | none         |       | none        |
| »»» from                            | string   | true     | none         |       | none        |
| »»» to                              | string   | true     | none         |       | none        |
| »» من 12:30 مساءً إلى 1:15 مساءً    | object   | false    | none         |       | none        |
| »»» from                            | string   | true     | none         |       | none        |
| »»» to                              | string   | true     | none         |       | none        |
| »» من 1:15 مساءً إلى 2:00 مساءً     | object   | false    | none         |       | none        |
| »»» from                            | string   | true     | none         |       | none        |
| »»» to                              | string   | true     | none         |       | none        |
| »» من 2:00 مساءً إلى 2:45 مساءً     | object   | false    | none         |       | none        |
| »»» from                            | string   | true     | none         |       | none        |
| »»» to                              | string   | true     | none         |       | none        |
| »» من 2:45 مساءً إلى 3:30 مساءً     | object   | false    | none         |       | none        |
| »»» from                            | string   | true     | none         |       | none        |
| »»» to                              | string   | true     | none         |       | none        |
| »» من 3:30 مساءً إلى 4:15 مساءً     | object   | false    | none         |       | none        |
| »»» from                            | string   | true     | none         |       | none        |
| »»» to                              | string   | true     | none         |       | none        |
| »» من 4:15 مساءً إلى 5:00 مساءً     | object   | false    | none         |       | none        |
| »»» from                            | string   | true     | none         |       | none        |
| »»» to                              | string   | true     | none         |       | none        |
| »» من 5:00 مساءً إلى 5:45 مساءً     | object   | false    | none         |       | none        |
| »»» from                            | string   | true     | none         |       | none        |
| »»» to                              | string   | true     | none         |       | none        |
| »» من 5:45 مساءً إلى 6:30 مساءً     | object   | false    | none         |       | none        |
| »»» from                            | string   | true     | none         |       | none        |
| »»» to                              | string   | true     | none         |       | none        |
| »» من 6:30 مساءً إلى 7:15 مساءً     | object   | false    | none         |       | none        |
| »»» from                            | string   | true     | none         |       | none        |
| »»» to                              | string   | true     | none         |       | none        |
| »» من 7:15 مساءً إلى 8:00 مساءً     | object   | false    | none         |       | none        |
| »»» from                            | string   | true     | none         |       | none        |
| »»» to                              | string   | true     | none         |       | none        |
| »» من 8:00 مساءً إلى 8:45 مساءً     | object   | false    | none         |       | none        |
| »»» from                            | string   | true     | none         |       | none        |
| »»» to                              | string   | true     | none         |       | none        |
| »» من 8:45 مساءً إلى 9:30 مساءً     | object   | false    | none         |       | none        |
| »»» from                            | string   | true     | none         |       | none        |
| »»» to                              | string   | true     | none         |       | none        |
| » errors                            | null     | true     | none         |       | none        |

# washing-cars/Cities & disctruct - المدن والمناطق

## GET Get Disctuct - جلب المناطق

GET /dynamic/districts

### Params

| Name    | Location | Type   | Required | Description |
| ------- | -------- | ------ | -------- | ----------- |
| city_id | query    | string | no       | none        |

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "تم استرجاع المناطق بنجاح",
    "data": {
        "data": [
            {
                "id": 1,
                "city_id": 1,
                "name_ar": "العليا",
                "name_en": "العليا",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 2,
                "city_id": 1,
                "name_ar": "الملز",
                "name_en": "الملز",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 3,
                "city_id": 1,
                "name_ar": "النرجس",
                "name_en": "النرجس",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 4,
                "city_id": 1,
                "name_ar": "الياسمين",
                "name_en": "الياسمين",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 5,
                "city_id": 1,
                "name_ar": "الورود",
                "name_en": "الورود",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 6,
                "city_id": 1,
                "name_ar": "الصحافة",
                "name_en": "الصحافة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 7,
                "city_id": 1,
                "name_ar": "الملقا",
                "name_en": "الملقا",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 8,
                "city_id": 1,
                "name_ar": "المروج",
                "name_en": "المروج",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 9,
                "city_id": 1,
                "name_ar": "النسيم",
                "name_en": "النسيم",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 10,
                "city_id": 1,
                "name_ar": "الروضة",
                "name_en": "الروضة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 11,
                "city_id": 1,
                "name_ar": "السليمانية",
                "name_en": "السليمانية",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 12,
                "city_id": 1,
                "name_ar": "المعذر",
                "name_en": "المعذر",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 13,
                "city_id": 1,
                "name_ar": "الغدير",
                "name_en": "الغدير",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 14,
                "city_id": 1,
                "name_ar": "الحمراء",
                "name_en": "الحمراء",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 15,
                "city_id": 1,
                "name_ar": "الشفا",
                "name_en": "الشفا",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 16,
                "city_id": 1,
                "name_ar": "الزهراء",
                "name_en": "الزهراء",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 17,
                "city_id": 1,
                "name_ar": "المنصورة",
                "name_en": "المنصورة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 18,
                "city_id": 1,
                "name_ar": "الندى",
                "name_en": "الندى",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 19,
                "city_id": 1,
                "name_ar": "الفيصلية",
                "name_en": "الفيصلية",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 20,
                "city_id": 1,
                "name_ar": "العزيزية",
                "name_en": "العزيزية",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 21,
                "city_id": 1,
                "name_ar": "الربوة",
                "name_en": "الربوة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 22,
                "city_id": 1,
                "name_ar": "الواحة",
                "name_en": "الواحة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 23,
                "city_id": 1,
                "name_ar": "الأندلس",
                "name_en": "الأندلس",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 24,
                "city_id": 1,
                "name_ar": "المحمدية",
                "name_en": "المحمدية",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 25,
                "city_id": 1,
                "name_ar": "الخليج",
                "name_en": "الخليج",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 26,
                "city_id": 1,
                "name_ar": "الديرة",
                "name_en": "الديرة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 27,
                "city_id": 1,
                "name_ar": "البطحاء",
                "name_en": "البطحاء",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 28,
                "city_id": 1,
                "name_ar": "الفوطة",
                "name_en": "الفوطة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 29,
                "city_id": 2,
                "name_ar": "الشاطئ",
                "name_en": "الشاطئ",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 30,
                "city_id": 2,
                "name_ar": "الكورنيش",
                "name_en": "الكورنيش",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 31,
                "city_id": 2,
                "name_ar": "الحمراء",
                "name_en": "الحمراء",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 32,
                "city_id": 2,
                "name_ar": "الروضة",
                "name_en": "الروضة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 33,
                "city_id": 2,
                "name_ar": "النزهة",
                "name_en": "النزهة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 34,
                "city_id": 2,
                "name_ar": "الصفا",
                "name_en": "الصفا",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 35,
                "city_id": 2,
                "name_ar": "المرجان",
                "name_en": "المرجان",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 36,
                "city_id": 2,
                "name_ar": "الزهراء",
                "name_en": "الزهراء",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 37,
                "city_id": 2,
                "name_ar": "الفيصلية",
                "name_en": "الفيصلية",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 38,
                "city_id": 2,
                "name_ar": "السلامة",
                "name_en": "السلامة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 39,
                "city_id": 2,
                "name_ar": "الربوة",
                "name_en": "الربوة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 40,
                "city_id": 2,
                "name_ar": "الأندلس",
                "name_en": "الأندلس",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 41,
                "city_id": 2,
                "name_ar": "الشرفية",
                "name_en": "الشرفية",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 42,
                "city_id": 2,
                "name_ar": "البغدادية",
                "name_en": "البغدادية",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 43,
                "city_id": 2,
                "name_ar": "النسيم",
                "name_en": "النسيم",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 44,
                "city_id": 2,
                "name_ar": "الصواري",
                "name_en": "الصواري",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 45,
                "city_id": 2,
                "name_ar": "الثغر",
                "name_en": "الثغر",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 46,
                "city_id": 2,
                "name_ar": "المحمدية",
                "name_en": "المحمدية",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 47,
                "city_id": 2,
                "name_ar": "الصالحية",
                "name_en": "الصالحية",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 48,
                "city_id": 2,
                "name_ar": "الجوهرة",
                "name_en": "الجوهرة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 49,
                "city_id": 2,
                "name_ar": "الواحة",
                "name_en": "الواحة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 50,
                "city_id": 5,
                "name_ar": "الفردوس",
                "name_en": "الفردوس",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 51,
                "city_id": 5,
                "name_ar": "الشاطئ",
                "name_en": "الشاطئ",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 52,
                "city_id": 5,
                "name_ar": "النورس",
                "name_en": "النورس",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 53,
                "city_id": 5,
                "name_ar": "الإسكان",
                "name_en": "الإسكان",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 54,
                "city_id": 5,
                "name_ar": "الجلوية",
                "name_en": "الجلوية",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 55,
                "city_id": 5,
                "name_ar": "العدامة",
                "name_en": "العدامة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 56,
                "city_id": 5,
                "name_ar": "البادية",
                "name_en": "البادية",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 57,
                "city_id": 5,
                "name_ar": "الفنار",
                "name_en": "الفنار",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 58,
                "city_id": 5,
                "name_ar": "السوق",
                "name_en": "السوق",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 59,
                "city_id": 5,
                "name_ar": "القادسية",
                "name_en": "القادسية",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 60,
                "city_id": 5,
                "name_ar": "الخليج",
                "name_en": "الخليج",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 61,
                "city_id": 5,
                "name_ar": "المطار",
                "name_en": "المطار",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 62,
                "city_id": 5,
                "name_ar": "الأحياء",
                "name_en": "الأحياء",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 63,
                "city_id": 5,
                "name_ar": "النهضة",
                "name_en": "النهضة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 64,
                "city_id": 3,
                "name_ar": "العزيزية",
                "name_en": "العزيزية",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 65,
                "city_id": 3,
                "name_ar": "النسيم",
                "name_en": "النسيم",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 66,
                "city_id": 3,
                "name_ar": "الشرائع",
                "name_en": "الشرائع",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 67,
                "city_id": 3,
                "name_ar": "المسفلة",
                "name_en": "المسفلة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 68,
                "city_id": 3,
                "name_ar": "أجياد",
                "name_en": "أجياد",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 69,
                "city_id": 3,
                "name_ar": "الطندباوي",
                "name_en": "الطندباوي",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 70,
                "city_id": 3,
                "name_ar": "الكعكية",
                "name_en": "الكعكية",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 71,
                "city_id": 3,
                "name_ar": "الهجلة",
                "name_en": "الهجلة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 72,
                "city_id": 3,
                "name_ar": "المعابدة",
                "name_en": "المعابدة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 73,
                "city_id": 3,
                "name_ar": "الحجون",
                "name_en": "الحجون",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 74,
                "city_id": 3,
                "name_ar": "جرول",
                "name_en": "جرول",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 75,
                "city_id": 3,
                "name_ar": "الزاهر",
                "name_en": "الزاهر",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 76,
                "city_id": 3,
                "name_ar": "الراشدية",
                "name_en": "الراشدية",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 77,
                "city_id": 3,
                "name_ar": "العتيبية",
                "name_en": "العتيبية",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 78,
                "city_id": 4,
                "name_ar": "العوالي",
                "name_en": "العوالي",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 79,
                "city_id": 4,
                "name_ar": "الحرم",
                "name_en": "الحرم",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 80,
                "city_id": 4,
                "name_ar": "باب المجيدي",
                "name_en": "باب المجيدي",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 81,
                "city_id": 4,
                "name_ar": "العنبرية",
                "name_en": "العنبرية",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 82,
                "city_id": 4,
                "name_ar": "الدويمة",
                "name_en": "الدويمة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 83,
                "city_id": 4,
                "name_ar": "السيح",
                "name_en": "السيح",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 84,
                "city_id": 4,
                "name_ar": "الجرف",
                "name_en": "الجرف",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 85,
                "city_id": 4,
                "name_ar": "الأزهري",
                "name_en": "الأزهري",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 86,
                "city_id": 4,
                "name_ar": "الدفاع",
                "name_en": "الدفاع",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 87,
                "city_id": 4,
                "name_ar": "البحر",
                "name_en": "البحر",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 88,
                "city_id": 4,
                "name_ar": "الإسكان",
                "name_en": "الإسكان",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 89,
                "city_id": 4,
                "name_ar": "طيبة",
                "name_en": "طيبة",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            },
            {
                "id": 90,
                "city_id": 4,
                "name_ar": "الملك فهد",
                "name_en": "الملك فهد",
                "code": null,
                "description_ar": null,
                "description_en": null,
                "is_active": true,
                "sort_order": 0,
                "latitude": null,
                "longitude": null,
                "metadata": null,
                "created_at": "2025-08-17T12:22:21.000000Z",
                "updated_at": "2025-08-17T12:22:21.000000Z"
            }
        ]
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name               | Type     | Required | Restrictions | Title | description |
| ------------------ | -------- | -------- | ------------ | ----- | ----------- |
| » success          | boolean  | true     | none         |       | none        |
| » message          | string   | true     | none         |       | none        |
| » data             | object   | true     | none         |       | none        |
| »» data            | [object] | true     | none         |       | none        |
| »»» id             | integer  | true     | none         |       | none        |
| »»» city_id        | integer  | true     | none         |       | none        |
| »»» name_ar        | string   | true     | none         |       | none        |
| »»» name_en        | string   | true     | none         |       | none        |
| »»» code           | null     | true     | none         |       | none        |
| »»» description_ar | null     | true     | none         |       | none        |
| »»» description_en | null     | true     | none         |       | none        |
| »»» is_active      | boolean  | true     | none         |       | none        |
| »»» sort_order     | integer  | true     | none         |       | none        |
| »»» latitude       | null     | true     | none         |       | none        |
| »»» longitude      | null     | true     | none         |       | none        |
| »»» metadata       | null     | true     | none         |       | none        |
| »»» created_at     | string   | true     | none         |       | none        |
| »»» updated_at     | string   | true     | none         |       | none        |
| » errors           | null     | true     | none         |       | none        |

## GET Get all cities - جلب المدن

GET /dynamic/cities

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "تم استرجاع المدن بنجاح",
    "data": {
        "data": [
            {
                "id": 1,
                "name_ar": "الرياض",
                "name_en": "Riyadh",
                "code": null,
                "is_active": true
            },
            {
                "id": 2,
                "name_ar": "جدة",
                "name_en": "Jeddah",
                "code": null,
                "is_active": true
            },
            {
                "id": 3,
                "name_ar": "مكة المكرمة",
                "name_en": "Mecca",
                "code": null,
                "is_active": true
            },
            {
                "id": 4,
                "name_ar": "المدينة المنورة",
                "name_en": "Medina",
                "code": null,
                "is_active": true
            },
            {
                "id": 5,
                "name_ar": "الدمام",
                "name_en": "Dammam",
                "code": null,
                "is_active": true
            },
            {
                "id": 6,
                "name_ar": "الخبر",
                "name_en": "Khobar",
                "code": null,
                "is_active": true
            },
            {
                "id": 7,
                "name_ar": "الظهران",
                "name_en": "Dhahran",
                "code": null,
                "is_active": true
            },
            {
                "id": 8,
                "name_ar": "الطائف",
                "name_en": "Taif",
                "code": null,
                "is_active": true
            },
            {
                "id": 9,
                "name_ar": "بريدة",
                "name_en": "Buraidah",
                "code": null,
                "is_active": true
            },
            {
                "id": 10,
                "name_ar": "تبوك",
                "name_en": "Tabuk",
                "code": null,
                "is_active": true
            },
            {
                "id": 11,
                "name_ar": "خميس مشيط",
                "name_en": "Khamis Mushait",
                "code": null,
                "is_active": true
            },
            {
                "id": 12,
                "name_ar": "حائل",
                "name_en": "Hail",
                "code": null,
                "is_active": true
            },
            {
                "id": 13,
                "name_ar": "الجبيل",
                "name_en": "Jubail",
                "code": null,
                "is_active": true
            },
            {
                "id": 14,
                "name_ar": "ينبع",
                "name_en": "Yanbu",
                "code": null,
                "is_active": true
            },
            {
                "id": 15,
                "name_ar": "أبها",
                "name_en": "Abha",
                "code": null,
                "is_active": true
            },
            {
                "id": 16,
                "name_ar": "نجران",
                "name_en": "Najran",
                "code": null,
                "is_active": true
            },
            {
                "id": 17,
                "name_ar": "الأحساء",
                "name_en": "Al-Ahsa",
                "code": null,
                "is_active": true
            },
            {
                "id": 18,
                "name_ar": "القطيف",
                "name_en": "Qatif",
                "code": null,
                "is_active": true
            },
            {
                "id": 19,
                "name_ar": "عنيزة",
                "name_en": "Unaizah",
                "code": null,
                "is_active": true
            },
            {
                "id": 20,
                "name_ar": "الرس",
                "name_en": "Ar Rass",
                "code": null,
                "is_active": true
            }
        ]
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name          | Type     | Required | Restrictions | Title | description |
| ------------- | -------- | -------- | ------------ | ----- | ----------- |
| » success     | boolean  | true     | none         |       | none        |
| » message     | string   | true     | none         |       | none        |
| » data        | object   | true     | none         |       | none        |
| »» data       | [object] | true     | none         |       | none        |
| »»» id        | integer  | true     | none         |       | none        |
| »»» name_ar   | string   | true     | none         |       | none        |
| »»» name_en   | string   | true     | none         |       | none        |
| »»» code      | null     | true     | none         |       | none        |
| »»» is_active | boolean  | true     | none         |       | none        |
| » errors      | null     | true     | none         |       | none        |

# washing-cars/Pacakges - الباقات

## GET get all packaegs

GET /packages

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "string",
    "data": {
        "data": [
            {
                "id": 0,
                "name_ar": "string",
                "name_en": "string",
                "description_ar": "string",
                "description_en": "string",
                "price": "string",
                "original_price": "string",
                "duration_days": 0,
                "wash_count": 0,
                "max_cars": 0,
                "is_active": true,
                "is_popular": true,
                "image_url": null,
                "icon_url": null,
                "included_services": null,
                "features": ["string"]
            }
        ]
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name                  | Type     | Required | Restrictions | Title | description |
| --------------------- | -------- | -------- | ------------ | ----- | ----------- |
| » success             | boolean  | true     | none         |       | none        |
| » message             | string   | true     | none         |       | none        |
| » data                | object   | true     | none         |       | none        |
| »» data               | [object] | true     | none         |       | none        |
| »»» id                | integer  | true     | none         |       | none        |
| »»» name_ar           | string   | true     | none         |       | none        |
| »»» name_en           | string   | true     | none         |       | none        |
| »»» description_ar    | string   | true     | none         |       | none        |
| »»» description_en    | string   | true     | none         |       | none        |
| »»» price             | string   | true     | none         |       | none        |
| »»» original_price    | string   | true     | none         |       | none        |
| »»» duration_days     | integer  | true     | none         |       | none        |
| »»» wash_count        | integer  | true     | none         |       | none        |
| »»» max_cars          | integer  | true     | none         |       | none        |
| »»» is_active         | boolean  | true     | none         |       | none        |
| »»» is_popular        | boolean  | true     | none         |       | none        |
| »»» image_url         | null     | true     | none         |       | none        |
| »»» icon_url          | null     | true     | none         |       | none        |
| »»» included_services | null     | true     | none         |       | none        |
| »»» features          | [string] | true     | none         |       | none        |
| » errors              | null     | true     | none         |       | none        |

## GET get package data

GET /packages/1

> Response Examples

> 200 Response

```json
{
    "success": true,
    "message": "تم استرجاع الباقة بنجاح",
    "data": {
        "data": {
            "id": 1,
            "name_ar": "الباقة الأسبوعية",
            "name_en": "Weekly Package",
            "description_ar": "باقة أسبوعية تشمل 3 مرات غسيل",
            "description_en": "Weekly package includes 3 washes",
            "price": "120.00",
            "original_price": "150.00",
            "duration_days": 7,
            "wash_count": 3,
            "max_cars": 1,
            "is_active": true,
            "is_popular": true,
            "image_url": null,
            "icon_url": null,
            "included_services": null,
            "features": [
                "غسيل خارجي شامل",
                "تجفيف تلقائي",
                "صيانة مجانية",
                "دعم فني 24/7"
            ]
        }
    },
    "errors": null
}
```

### Responses

| HTTP Status Code | Meaning                                                 | Description | Data schema |
| ---------------- | ------------------------------------------------------- | ----------- | ----------- |
| 200              | [OK](https://tools.ietf.org/html/rfc7231#section-6.3.1) | none        | Inline      |

### Responses Data Schema

HTTP Status Code **200**

| Name                  | Type     | Required | Restrictions | Title | description |
| --------------------- | -------- | -------- | ------------ | ----- | ----------- |
| » success             | boolean  | true     | none         |       | none        |
| » message             | string   | true     | none         |       | none        |
| » data                | object   | true     | none         |       | none        |
| »» data               | object   | true     | none         |       | none        |
| »»» id                | integer  | true     | none         |       | none        |
| »»» name_ar           | string   | true     | none         |       | none        |
| »»» name_en           | string   | true     | none         |       | none        |
| »»» description_ar    | string   | true     | none         |       | none        |
| »»» description_en    | string   | true     | none         |       | none        |
| »»» price             | string   | true     | none         |       | none        |
| »»» original_price    | string   | true     | none         |       | none        |
| »»» duration_days     | integer  | true     | none         |       | none        |
| »»» wash_count        | integer  | true     | none         |       | none        |
| »»» max_cars          | integer  | true     | none         |       | none        |
| »»» is_active         | boolean  | true     | none         |       | none        |
| »»» is_popular        | boolean  | true     | none         |       | none        |
| »»» image_url         | null     | true     | none         |       | none        |
| »»» icon_url          | null     | true     | none         |       | none        |
| »»» included_services | null     | true     | none         |       | none        |
| »»» features          | [string] | true     | none         |       | none        |
| » errors              | null     | true     | none         |       | none        |

# Data Schema
