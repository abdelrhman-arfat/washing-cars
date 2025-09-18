# API Documentation
This document provides an overview of the API routes for the [washing-cars project](https://abdelrhman-arfat.github.io/washing-cars/).
# API Documentation

## Authentication

### Register User

- **URL**: `POST /api/auth/register`
- **Description**: Register a new user account
- **Request Body**:
    ```json
    {
        "name": "string",
        "phone": "string",
        "password": "string"
    }
    ```
- **Response**: 201 Created
    ```json
    {
        "success": true,
        "message": "register success",
        "data": {
            "user": {
                "id": 1,
                "name": "string",
                "phone": "string",
                "email": "string",
                "role": "customer",
                "wallet_balance": 0
            },
            "token": "string",
            "verification_code": "string",
            "token_type": "Bearer"
        }
    }
    ```

### Login User

- **URL**: `POST /api/auth/login`
- **Description**: Authenticate user and get access token
- **Request Body**:
    ```json
    {
        "phone": "string",
        "password": "string"
    }
    ```
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "login success",
        "data": {
            "user": {
                "id": 1,
                "name": "string",
                "phone": "string",
                "email": "string",
                "role": "customer",
                "wallet_balance": 0
            },
            "token": "string",
            "token_type": "Bearer"
        }
    }
    ```

## User Management

### Get User Profile

- **URL**: `GET /api/user/profile`
- **Description**: Get authenticated user profile
- **Headers**: `Authorization: Bearer {token}`
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "profile success",
        "data": {
            "user": {
                "id": 1,
                "name": "string",
                "phone": "string",
                "email": "string",
                "role": "customer",
                "wallet_balance": 0,
                "profile_image": "string",
                "last_login_at": "datetime"
            }
        }
    }
    ```

### Update User Profile

- **URL**: `PUT /api/user/profile`
- **Description**: Update authenticated user profile
- **Headers**: `Authorization: Bearer {token}`
- **Request Body**:
    ```json
    {
        "name": "string",
        "email": "string"
    }
    ```
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "update profile success",
        "data": {
            "user": {
                "id": 1,
                "name": "string",
                "phone": "string",
                "email": "string",
                "role": "customer",
                "wallet_balance": 0,
                "profile_image": "string",
                "last_login_at": "datetime"
            }
        }
    }
    ```

### Change Password

- **URL**: `PUT /api/user/change-password`
- **Description**: Change user password
- **Headers**: `Authorization: Bearer {token}`
- **Request Body**:
    ```json
    {
        "current_password": "string",
        "password": "string",
        "password_confirmation": "string"
    }
    ```
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "change password success",
        "data": null
    }
    ```

### Logout

- **URL**: `POST /api/user/logout`
- **Description**: Logout user and invalidate token
- **Headers**: `Authorization: Bearer {token}`
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "logout success",
        "data": null
    }
    ```

### Refresh Token

- **URL**: `POST /api/user/refresh`
- **Description**: Refresh access token
- **Headers**: `Authorization: Bearer {token}`
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "refresh token success",
        "data": {
            "token": "string",
            "token_type": "Bearer"
        }
    }
    ```

## Phone Verification

### Resend OTP

- **URL**: `POST /api/user/resend-otp`
- **Description**: Resend verification code to user's phone
- **Headers**: `Authorization: Bearer {token}`
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "resend otp success",
        "data": {
            "verification_code": "string"
        }
    }
    ```

### Verify OTP

- **URL**: `POST /api/user/verify-otp`
- **Description**: Verify phone number with OTP code
- **Headers**: `Authorization: Bearer {token}`
- **Request Body**:
    ```json
    {
        "verification_code": "string"
    }
    ```
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "verify otp success",
        "data": null
    }
    ```

## Car Management

### Get All Cars

- **URL**: `GET /api/cars`
- **Description**: Get all cars for authenticated user
- **Headers**: `Authorization: Bearer {token}`
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "cars retrieved successfully",
        "data": {
            "data": [
                {
                    "id": 1,
                    "user_id": 1,
                    "brand_id": 1,
                    "type_id": 1,
                    "plate_number": "ABC-123",
                    "model_year": 2020,
                    "color": "Red",
                    "notes": "string",
                    "is_default": true,
                    "created_at": "datetime",
                    "updated_at": "datetime",
                    "brand": {
                        "id": 1,
                        "name": "Toyota"
                    },
                    "type": {
                        "id": 1,
                        "name": "Sedan"
                    }
                }
            ],
            "total": 1
        }
    }
    ```

### Get Specific Car

- **URL**: `GET /api/cars/{id}`
- **Description**: Get specific car by ID
- **Headers**: `Authorization: Bearer {token}`
- **Parameters**: `id` - Car ID
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "car retrieved successfully",
        "data": {
            "data": {
                "id": 1,
                "user_id": 1,
                "brand_id": 1,
                "type_id": 1,
                "plate_number": "ABC-123",
                "model_year": 2020,
                "color": "Red",
                "notes": "string",
                "is_default": true,
                "created_at": "datetime",
                "updated_at": "datetime",
                "brand": {
                    "id": 1,
                    "name": "Toyota"
                },
                "type": {
                    "id": 1,
                    "name": "Sedan"
                }
            }
        }
    }
    ```

### Create New Car

- **URL**: `POST /api/cars`
- **Description**: Create a new car for authenticated user
- **Headers**: `Authorization: Bearer {token}`
- **Request Body**:
    ```json
    {
        "brand_id": 1,
        "type_id": 1,
        "plate_number": "ABC-123",
        "model_year": 2020,
        "color": "Red",
        "notes": "string",
        "is_default": false
    }
    ```
- **Validation Rules**:
    - `brand_id`: required, exists in brands table
    - `type_id`: required, exists in types table
    - `plate_number`: required, string, max 20 chars, unique per user
    - `model_year`: required, integer, min 1900, max current year + 1
    - `color`: required, string, max 50 chars
    - `notes`: nullable, string, max 500 chars
    - `is_default`: boolean
- **Response**: 201 Created
    ```json
    {
        "success": true,
        "message": "car created successfully",
        "data": {
            "data": {
                "id": 1,
                "user_id": 1,
                "brand_id": 1,
                "type_id": 1,
                "plate_number": "ABC-123",
                "model_year": 2020,
                "color": "Red",
                "notes": "string",
                "is_default": true,
                "created_at": "datetime",
                "updated_at": "datetime",
                "brand": {
                    "id": 1,
                    "name": "Toyota"
                },
                "type": {
                    "id": 1,
                    "name": "Sedan"
                }
            }
        }
    }
    ```

### Update Car

- **URL**: `PUT /api/cars/{id}`
- **Description**: Update existing car
- **Headers**: `Authorization: Bearer {token}`
- **Parameters**: `id` - Car ID
- **Request Body**:
    ```json
    {
        "brand_id": 1,
        "type_id": 1,
        "plate_number": "ABC-123",
        "model_year": 2020,
        "color": "Blue",
        "notes": "Updated notes",
        "is_default": false
    }
    ```
- **Validation Rules**: Same as create, but all fields are optional
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "car updated successfully",
        "data": {
            "data": {
                "id": 1,
                "user_id": 1,
                "brand_id": 1,
                "type_id": 1,
                "plate_number": "ABC-123",
                "model_year": 2020,
                "color": "Blue",
                "notes": "Updated notes",
                "is_default": false,
                "created_at": "datetime",
                "updated_at": "datetime",
                "brand": {
                    "id": 1,
                    "name": "Toyota"
                },
                "type": {
                    "id": 1,
                    "name": "Sedan"
                }
            }
        }
    }
    ```

### Delete Car

- **URL**: `DELETE /api/cars/{id}`
- **Description**: Delete car by ID
- **Headers**: `Authorization: Bearer {token}`
- **Parameters**: `id` - Car ID
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "car deleted successfully",
        "data": null
    }
    ```

### Set Car as Default

- **URL**: `PATCH /api/cars/{id}/set-default`
- **Description**: Set car as default for user
- **Headers**: `Authorization: Bearer {token}`
- **Parameters**: `id` - Car ID
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "car set as default successfully",
        "data": {
            "data": {
                "id": 1,
                "user_id": 1,
                "brand_id": 1,
                "type_id": 1,
                "plate_number": "ABC-123",
                "model_year": 2020,
                "color": "Red",
                "notes": "string",
                "is_default": true,
                "created_at": "datetime",
                "updated_at": "datetime",
                "brand": {
                    "id": 1,
                    "name": "Toyota"
                },
                "type": {
                    "id": 1,
                    "name": "Sedan"
                }
            }
        }
    }
    ```
## Types and Brands Management

### Overview
The Types and Brands API allow user to show the brands and types fo the cars

**Base URL** : `/api'

### Get All Brands
 **URL**: `GET /api/brands`
- **Description**: Get all brands
- **Headers**: `Authorization: Bearer {token}`
- **Response**: 200 OK
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
### Get All Types
 **URL**: `GET /api/types`
- **Description**: Get all brands
- **Headers**: `Authorization: Bearer {token}`
- **Response**: 200 OK
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


## Address Management

### Overview

The Address Management API allows users to manage their delivery addresses. All endpoints require authentication and phone verification.

**Base URL**: `/api/addresses`

**Authentication**: All endpoints require `Authorization: Bearer {token}` header

**Phone Verification**: All endpoints require verified phone number

### Get All Addresses

- **URL**: `GET /api/addresses`
- **Description**: Get all addresses for authenticated user
- **Headers**: `Authorization: Bearer {token}`
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "addresses retrieved successfully",
        "data": {
            "data": [
                {
                    "id": 1,
                    "user_id": 1,
                    "district_id": 1,
                    "address_name": "المنزل",
                    "full_address": "شارع الملك فهد، حي النزهة، الرياض",
                    "building_number": "123",
                    "street_name": "شارع الملك فهد",
                    "neighborhood": "حي النزهة",
                    "latitude": 24.7136,
                    "longitude": 46.6753,
                    "is_default": true,
                    "additional_instructions": "بجانب مسجد النور",
                    "created_at": "2024-01-01T00:00:00.000000Z",
                    "updated_at": "2024-01-01T00:00:00.000000Z",
                    "district": {
                        "id": 1,
                        "name": "النزهة",
                        "city": {
                            "id": 1,
                            "name": "الرياض"
                        }
                    }
                }
            ],
            "total": 1
        }
    }
    ```

### Get Specific Address

- **URL**: `GET /api/addresses/{id}`
- **Description**: Get specific address by ID
- **Headers**: `Authorization: Bearer {token}`
- **Parameters**: `id` - Address ID
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "address retrieved successfully",
        "data": {
            "data": {
                "id": 1,
                "user_id": 1,
                "district_id": 1,
                "address_name": "المنزل",
                "full_address": "شارع الملك فهد، حي النزهة، الرياض",
                "building_number": "123",
                "street_name": "شارع الملك فهد",
                "neighborhood": "حي النزهة",
                "latitude": 24.7136,
                "longitude": 46.6753,
                "is_default": true,
                "additional_instructions": "بجانب مسجد النور",
                "created_at": "2024-01-01T00:00:00.000000Z",
                "updated_at": "2024-01-01T00:00:00.000000Z",
                "district": {
                    "id": 1,
                    "name": "النزهة",
                    "city": {
                        "id": 1,
                        "name": "الرياض"
                    }
                }
            }
        }
    }
    ```

### Create New Address

- **URL**: `POST /api/addresses`
- **Description**: Create a new address for authenticated user
- **Headers**: `Authorization: Bearer {token}`
- **Request Body**:
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
- **Validation Rules**:
    - `district_id`: required, exists in districts table
    - `address_name`: required, string, max 100 characters
    - `full_address`: required, string, max 500 characters
    - `building_number`: nullable, string, max 20 characters
    - `street_name`: nullable, string, max 200 characters
    - `neighborhood`: nullable, string, max 100 characters
    - `latitude`: nullable, numeric, between -90 and 90
    - `longitude`: nullable, numeric, between -180 and 180
    - `is_default`: boolean
    - `additional_instructions`: nullable, string, max 1000 characters
- **Response**: 201 Created
    ```json
    {
        "success": true,
        "message": "address created successfully",
        "data": {
            "data": {
                "id": 1,
                "user_id": 1,
                "district_id": 1,
                "address_name": "المنزل",
                "full_address": "شارع الملك فهد، حي النزهة، الرياض",
                "building_number": "123",
                "street_name": "شارع الملك فهد",
                "neighborhood": "حي النزهة",
                "latitude": 24.7136,
                "longitude": 46.6753,
                "is_default": true,
                "additional_instructions": "بجانب مسجد النور",
                "created_at": "2024-01-01T00:00:00.000000Z",
                "updated_at": "2024-01-01T00:00:00.000000Z",
                "district": {
                    "id": 1,
                    "name": "النزهة",
                    "city": {
                        "id": 1,
                        "name": "الرياض"
                    }
                }
            }
        }
    }
    ```

### Update Address

- **URL**: `PUT /api/addresses/{id}`
- **Description**: Update existing address
- **Headers**: `Authorization: Bearer {token}`
- **Parameters**: `id` - Address ID
- **Request Body**:
    ```json
    {
        "address_name": "العمل",
        "additional_instructions": "محدث"
    }
    ```
- **Validation Rules**: Same as create, but all fields are optional
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "address updated successfully",
        "data": {
            "data": {
                "id": 1,
                "user_id": 1,
                "district_id": 1,
                "address_name": "العمل",
                "full_address": "شارع الملك فهد، حي النزهة، الرياض",
                "building_number": "123",
                "street_name": "شارع الملك فهد",
                "neighborhood": "حي النزهة",
                "latitude": 24.7136,
                "longitude": 46.6753,
                "is_default": true,
                "additional_instructions": "محدث",
                "created_at": "2024-01-01T00:00:00.000000Z",
                "updated_at": "2024-01-01T00:00:00.000000Z",
                "district": {
                    "id": 1,
                    "name": "النزهة",
                    "city": {
                        "id": 1,
                        "name": "الرياض"
                    }
                }
            }
        }
    }
    ```

### Delete Address

- **URL**: `DELETE /api/addresses/{id}`
- **Description**: Delete address by ID
- **Headers**: `Authorization: Bearer {token}`
- **Parameters**: `id` - Address ID
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "address deleted successfully",
        "data": null
    }
    ```

### Set Address as Default

- **URL**: `PATCH /api/addresses/{id}/set-default`
- **Description**: Set address as default for user
- **Headers**: `Authorization: Bearer {token}`
- **Parameters**: `id` - Address ID
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "address set as default successfully",
        "data": {
            "data": {
                "id": 1,
                "user_id": 1,
                "district_id": 1,
                "address_name": "المنزل",
                "full_address": "شارع الملك فهد، حي النزهة، الرياض",
                "building_number": "123",
                "street_name": "شارع الملك فهد",
                "neighborhood": "حي النزهة",
                "latitude": 24.7136,
                "longitude": 46.6753,
                "is_default": true,
                "additional_instructions": "بجانب مسجد النور",
                "created_at": "2024-01-01T00:00:00.000000Z",
                "updated_at": "2024-01-01T00:00:00.000000Z",
                "district": {
                    "id": 1,
                    "name": "النزهة",
                    "city": {
                        "id": 1,
                        "name": "الرياض"
                    }
                }
            }
        }
    }
    ```

## Orders Management

### Get User Orders

- **URL**: `GET /api/orders`
- **Description**: Get authenticated user orders with pagination and filtering
- **Headers**: `Authorization: Bearer {token}`
- **Query Parameters**:
    - `status` (optional): Filter by order status (pending, confirmed, completed, cancelled)
    - `payment_status` (optional): Filter by payment status (pending, paid, failed, refunded)
    - `per_page` (optional): Number of orders per page (1-100, default: 15)
    - `search` (optional): Search in order number or notes
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "Orders retrieved successfully",
        "data": {
            "orders": [
                {
                    "id": 1,
                    "order_number": "ORD-20241201-ABC123",
                    "status": "pending",
                    "payment_status": "pending",
                    "total_price": 50.0,
                    "service_price": 50.0,
                    "addons_price": 0.0,
                    "discount_amount": 0.0,
                    "booking_datetime": "2024-12-01T10:00:00.000000Z",
                    "estimated_start_time": "2024-12-01T10:30:00.000000Z",
                    "actual_start_time": null,
                    "completed_at": null,
                    "payment_method": "cash",
                    "notes": "Test order",
                    "delegate_notes": null,
                    "cancellation_reason": null,
                    "service": {
                        "id": 1,
                        "name": "غسيل السيارة",
                        "price": 50.0,
                        "duration_minutes": 30
                    },
                    "package": null,
                    "car": {
                        "id": 1,
                        "plate_number": "ABC123",
                        "model_year": 2020,
                        "color": "أبيض"
                    },
                    "address": {
                        "id": 1,
                        "address_name": "المنزل",
                        "full_address": "شارع الملك فهد، الرياض"
                    },
                    "delegate": null,
                    "addons": [],
                    "rating": null,
                    "created_at": "2024-12-01T09:00:00.000000Z",
                    "updated_at": "2024-12-01T09:00:00.000000Z"
                }
            ],
            "pagination": {
                "current_page": 1,
                "last_page": 1,
                "per_page": 15,
                "total": 1,
                "from": 1,
                "to": 1
            }
        }
    }
    ```

### Get Specific Order

- **URL**: `GET /api/orders/{id}`
- **Description**: Get detailed information about a specific order
- **Headers**: `Authorization: Bearer {token}`
- **Response**: 200 OK
    ```json
    {
        "success": true,
        "message": "Order details retrieved successfully",
        "data": {
            "id": 1,
            "order_number": "ORD-20241201-ABC123",
            "status": "pending",
            "payment_status": "pending",
            "total_price": 50.0,
            "service_price": 50.0,
            "addons_price": 0.0,
            "discount_amount": 0.0,
            "booking_datetime": "2024-12-01T10:00:00.000000Z",
            "estimated_start_time": "2024-12-01T10:30:00.000000Z",
            "actual_start_time": null,
            "completed_at": null,
            "payment_method": "cash",
            "notes": "Test order",
            "delegate_notes": null,
            "cancellation_reason": null,
            "delegate_latitude": null,
            "delegate_longitude": null,
            "delegate_location_updated_at": null,
            "service": {
                "id": 1,
                "name": "غسيل السيارة",
                "description": "غسيل شامل للسيارة",
                "price": 50.0,
                "duration_minutes": 30,
                "image_url": "http://example.com/images/service.jpg"
            },
            "package": null,
            "car": {
                "id": 1,
                "plate_number": "ABC123",
                "model_year": 2020,
                "color": "أبيض",
                "notes": "سيارة عائلية"
            },
            "address": {
                "id": 1,
                "address_name": "المنزل",
                "full_address": "شارع الملك فهد، الرياض",
                "latitude": 24.7136,
                "longitude": 46.6753
            },
            "delegate": null,
            "addons": [],
            "transactions": [],
            "rating": null,
            "coupon": null,
            "created_at": "2024-12-01T09:00:00.000000Z",
            "updated_at": "2024-12-01T09:00:00.000000Z"
        }
    }
    ```

### Create New Order

- **URL**: `POST /api/orders`
- **Description**: Create a new order
- **Headers**: `Authorization: Bearer {token}`
-   -

## Error Responses

### 401 Unauthorized

```json
{
    "success": false,
    "message": "Unauthenticated.",
    "data": null
}
```

### 403 Forbidden

```json
{
    "success": false,
    "message": "Phone not verified",
    "data": null
}
```

### 404 Not Found

```json
{
    "success": false,
    "message": "address not found",
    "data": null
}
```

### 422 Validation Error

```json
{
    "success": false,
    "message": "Validation errors",
    "data": {
        "district_id": ["The district field is required."],
        "address_name": ["The address name field is required."]
    }
}
```

### 500 Internal Server Error

```json
{
    "success": false,
    "message": "an error occurred",
    "data": "Error details"
}
```



# Orders API

## Overview

The Orders API allows customers to manage their car wash orders and delegates to handle assigned orders.

## Order Statuses

- `pending` - Order is created but not yet confirmed
- `confirmed` - Order is confirmed and assigned to delegate
- `in_progress` - Delegate is working on the order
- `completed` - Order is completed
- `cancelled` - Order is cancelled

## Payment Statuses

- `pending` - Payment not yet processed
- `paid` - Payment completed
- `failed` - Payment failed

## Payment Methods

- `cash` - Cash payment
- `wallet` - Wallet payment
- `online` - Online payment
- `card` - Card payment

---

## 1. Get User Orders

### Endpoint

```
GET /orders
```

### Description

Retrieve paginated list of user orders with filtering and search capabilities.

### Authentication

Required

### Query Parameters

| Parameter        | Type    | Required | Description                                                                    |
| ---------------- | ------- | -------- | ------------------------------------------------------------------------------ |
| `status`         | string  | No       | Filter by order status (pending, confirmed, in_progress, completed, cancelled) |
| `payment_status` | string  | No       | Filter by payment status (pending, paid, failed)                               |
| `search`         | string  | No       | Search in order number or notes                                                |
| `per_page`       | integer | No       | Number of items per page (default: 15)                                         |
| `page`           | integer | No       | Page number (default: 1)                                                       |

### Response

```json
{
    "success": true,
    "message": "Orders retrieved successfully",
    "data": {
        "orders": [
            {
                "id": 1,
                "order_number": "ORD-2024-001",
                "status": "pending",
                "payment_status": "pending",
                "total_price": 75.0,
                "service_price": 50.0,
                "addons_price": 25.0,
                "discount_amount": 0.0,
                "booking_datetime": "2024-01-15T10:00:00Z",
                "estimated_start_time": "2024-01-15T10:30:00Z",
                "actual_start_time": null,
                "completed_at": null,
                "payment_method": "cash",
                "notes": "Please be careful with the paint",
                "delegate_notes": null,
                "cancellation_reason": null,
                "service": {
                    "id": 1,
                    "name": "غسيل خارجي وداخلي",
                    "price": 50.0,
                    "duration_minutes": 45
                },
                "package": null,
                "car": {
                    "id": 1,
                    "plate_number": "ABC-123",
                    "model_year": 2020,
                    "color": "أبيض"
                },
                "address": {
                    "id": 1,
                    "address_name": "المنزل",
                    "full_address": "شارع الملك فهد، الرياض"
                },
                "delegate": null,
                "addons": [
                    {
                        "id": 1,
                        "name": "تلميع الشمع",
                        "price": 25.0,
                        "quantity": 1
                    }
                ],
                "rating": null,
                "created_at": "2024-01-15T09:30:00Z",
                "updated_at": "2024-01-15T09:30:00Z"
            }
        ],
        "pagination": {
            "current_page": 1,
            "last_page": 3,
            "per_page": 15,
            "total": 45,
            "from": 1,
            "to": 15
        }
    }
}
```

### Error Responses

```json
{
    "success": false,
    "message": "Failed to retrieve orders",
    "data": null
}
```

---

## 2. Get Specific Order

### Endpoint

```
GET /orders/{id}
```

### Description

Retrieve detailed information about a specific order.

### Authentication

Required

### URL Parameters

| Parameter | Type    | Required | Description |
| --------- | ------- | -------- | ----------- |
| `id`      | integer | Yes      | Order ID    |

### Response

```json
{
    "success": true,
    "message": "Order details retrieved successfully",
    "data": {
        "id": 1,
        "order_number": "ORD-2024-001",
        "status": "pending",
        "payment_status": "pending",
        "total_price": 75.0,
        "service_price": 50.0,
        "addons_price": 25.0,
        "discount_amount": 0.0,
        "booking_datetime": "2024-01-15T10:00:00Z",
        "estimated_start_time": "2024-01-15T10:30:00Z",
        "actual_start_time": null,
        "completed_at": null,
        "payment_method": "cash",
        "notes": "Please be careful with the paint",
        "delegate_notes": null,
        "cancellation_reason": null,
        "service": {
            "id": 1,
            "name": "غسيل خارجي وداخلي",
            "description": "غسيل شامل للخارج والداخل مع تنظيف المقاعد",
            "price": 50.0,
            "duration_minutes": 45,
            "image_url": "https://example.com/service1.jpg"
        },
        "package": null,
        "car": {
            "id": 1,
            "plate_number": "ABC-123",
            "model_year": 2020,
            "color": "أبيض",
            "notes": "سيارة جديدة"
        },
        "address": {
            "id": 1,
            "address_name": "المنزل",
            "full_address": "شارع الملك فهد، الرياض",
            "latitude": 24.7136,
            "longitude": 46.6753
        },
        "delegate": {
            "id": 1,
            "name": "أحمد محمد",
            "phone": "+966501234567",
            "email": "ahmed@example.com",
            "profile_image": "https://example.com/delegate1.jpg"
        },
        "addons": [
            {
                "id": 1,
                "name": "تلميع الشمع",
                "description": "تلميع شامل مع شمع حماية",
                "price": 25.0,
                "image_url": "https://example.com/addon1.jpg",
                "quantity": 1
            }
        ],
        "transactions": [
            {
                "id": 1,
                "amount": 75.0,
                "type": "payment",
                "status": "completed",
                "payment_method": "cash",
                "created_at": "2024-01-15T09:30:00Z"
            }
        ],
        "rating": {
            "rating_score": 5,
            "comment": "خدمة ممتازة",
            "created_at": "2024-01-15T11:00:00Z"
        },
        "coupon": {
            "id": 1,
            "code": "SAVE10",
            "type": "percentage",
            "value": 10
        },
        "created_at": "2024-01-15T09:30:00Z",
        "updated_at": "2024-01-15T09:30:00Z"
    }
}
```

### Error Responses

```json
{
    "success": false,
    "message": "Order not found",
    "data": null
}
```

---

## 3. Create New Order

### Endpoint

```
POST /orders
```

### Description

Create a new car wash order.

### Authentication

Required

### Request Body

| Parameter          | Type     | Required | Description                                 |
| ------------------ | -------- | -------- | ------------------------------------------- |
| `service_id`       | integer  | Yes      | Service ID                                  |
| `package_id`       | integer  | No       | Package ID (optional)                       |
| `car_id`           | integer  | Yes      | Car ID (must belong to user)                |
| `address_id`       | integer  | Yes      | Address ID (must belong to user)            |
| `booking_datetime` | datetime | Yes      | Booking date and time (must be in future)   |
| `addon_ids`        | array    | No       | Array of addon service IDs                  |
| `coupon_code`      | string   | No       | Coupon code for discount                    |
| `payment_method`   | string   | Yes      | Payment method (cash, wallet, online, card) |
| `notes`            | string   | No       | Additional notes (max 500 characters)       |

### Request Example

```json
{
    "service_id": 1,
    "package_id": 2,
    "car_id": 1,
    "address_id": 1,
    "booking_datetime": "2024-01-15T10:00:00Z",
    "addon_ids": [1, 2],
    "coupon_code": "SAVE10",
    "payment_method": "wallet",
    "notes": "Please be careful with the paint"
}
```

### Response

```json
{
    "success": true,
    "message": "Order created successfully",
    "data": {
        "id": 1,
        "order_number": "ORD-2024-001",
        "status": "pending",
        "payment_status": "paid",
        "total_price": 67.5,
        "service_price": 100.0,
        "addons_price": 50.0,
        "discount_amount": 15.0,
        "booking_datetime": "2024-01-15T10:00:00Z",
        "estimated_start_time": "2024-01-15T10:30:00Z",
        "payment_method": "wallet",
        "notes": "Please be careful with the paint",
        "service": {
            "id": 1,
            "name": "غسيل شامل",
            "price": 100.0,
            "duration_minutes": 75
        },
        "package": {
            "id": 2,
            "name": "باقة VIP",
            "price": 100.0
        },
        "car": {
            "id": 1,
            "plate_number": "ABC-123",
            "model_year": 2020,
            "color": "أبيض"
        },
        "address": {
            "id": 1,
            "address_name": "المنزل",
            "full_address": "شارع الملك فهد، الرياض"
        },
        "addons": [
            {
                "id": 1,
                "name": "تلميع الشمع",
                "price": 25.0,
                "quantity": 1
            },
            {
                "id": 2,
                "name": "تنظيف المحرك",
                "price": 25.0,
                "quantity": 1
            }
        ],
        "coupon": {
            "id": 1,
            "code": "SAVE10",
            "type": "percentage",
            "value": 10
        },
        "created_at": "2024-01-15T09:30:00Z",
        "updated_at": "2024-01-15T09:30:00Z"
    }
}
```

### Error Responses

#### Validation Error (422)

```json
{
    "success": false,
    "message": "Validation failed",
    "data": {
        "service_id": ["معرف الخدمة مطلوب"],
        "booking_datetime": ["تاريخ ووقت الحجز يجب أن يكون في المستقبل"]
    }
}
```

#### Insufficient Balance (400)

```json
{
    "success": false,
    "message": "Insufficient wallet balance",
    "data": null
}
```

#### Invalid Coupon (400)

```json
{
    "success": false,
    "message": "Invalid or expired coupon code",
    "data": null
}
```

---

## 4. Update Order

### Endpoint

```
PUT /orders/{id}
```

### Description

Update an existing order. Customers can only update pending orders, while delegates can update location and notes.

### Authentication

Required

### URL Parameters

| Parameter | Type    | Required | Description |
| --------- | ------- | -------- | ----------- |
| `id`      | integer | Yes      | Order ID    |

### Request Body (Customer)

| Parameter          | Type     | Required | Description                                   |
| ------------------ | -------- | -------- | --------------------------------------------- |
| `notes`            | string   | No       | Additional notes (max 500 characters)         |
| `booking_datetime` | datetime | No       | New booking date and time (must be in future) |

### Request Body (Delegate)

| Parameter            | Type   | Required | Description                         |
| -------------------- | ------ | -------- | ----------------------------------- |
| `delegate_notes`     | string | No       | Delegate notes (max 500 characters) |
| `delegate_latitude`  | float  | No       | Current latitude (-90 to 90)        |
| `delegate_longitude` | float  | No       | Current longitude (-180 to 180)     |

### Request Example (Customer)

```json
{
    "notes": "Updated notes",
    "booking_datetime": "2024-01-15T11:00:00Z"
}
```

### Request Example (Delegate)

```json
{
    "delegate_notes": "On my way to location",
    "delegate_latitude": 24.7136,
    "delegate_longitude": 46.6753
}
```

### Response

```json
{
    "success": true,
    "message": "Order updated successfully",
    "data": {
        "id": 1,
        "order_number": "ORD-2024-001",
        "status": "pending",
        "payment_status": "pending",
        "total_price": 75.0,
        "service_price": 50.0,
        "addons_price": 25.0,
        "discount_amount": 0.0,
        "booking_datetime": "2024-01-15T11:00:00Z",
        "notes": "Updated notes",
        "delegate_notes": "On my way to location",
        "delegate_latitude": 24.7136,
        "delegate_longitude": 46.6753,
        "delegate_location_updated_at": "2024-01-15T10:15:00Z",
        "service": {
            "id": 1,
            "name": "غسيل خارجي وداخلي",
            "price": 50.0,
            "duration_minutes": 45
        },
        "car": {
            "id": 1,
            "plate_number": "ABC-123",
            "model_year": 2020,
            "color": "أبيض"
        },
        "address": {
            "id": 1,
            "address_name": "المنزل",
            "full_address": "شارع الملك فهد، الرياض"
        },
        "created_at": "2024-01-15T09:30:00Z",
        "updated_at": "2024-01-15T10:15:00Z"
    }
}
```

### Error Responses

```json
{
    "success": false,
    "message": "Order not found or cannot be updated",
    "data": null
}
```

---

## 5. Delete Order

### Endpoint

```
DELETE /orders/{id}
```

### Description

Delete an order. Only pending orders can be deleted.

### Authentication

Required

### URL Parameters

| Parameter | Type    | Required | Description |
| --------- | ------- | -------- | ----------- |
| `id`      | integer | Yes      | Order ID    |

### Response

```json
{
    "success": true,
    "message": "Order deleted successfully",
    "data": null
}
```

### Error Responses

```json
{
    "success": false,
    "message": "Order not found or cannot be deleted",
    "data": null
}
```

---

## 6. Cancel Order

### Endpoint

```
PATCH /orders/{id}/cancel
```

### Description

Cancel an order. Only pending, confirmed, or in-progress orders can be cancelled.

### Authentication

Required

### URL Parameters

| Parameter | Type    | Required | Description |
| --------- | ------- | -------- | ----------- |
| `id`      | integer | Yes      | Order ID    |

### Request Body

| Parameter             | Type   | Required | Description                                  |
| --------------------- | ------ | -------- | -------------------------------------------- |
| `cancellation_reason` | string | No       | Reason for cancellation (max 500 characters) |

### Request Example

```json
{
    "cancellation_reason": "Change of plans"
}
```

### Response

```json
{
    "success": true,
    "message": "Order cancelled successfully",
    "data": {
        "id": 1,
        "order_number": "ORD-2024-001",
        "status": "cancelled",
        "payment_status": "pending",
        "total_price": 75.0,
        "cancellation_reason": "Change of plans",
        "service": {
            "id": 1,
            "name": "غسيل خارجي وداخلي",
            "price": 50.0,
            "duration_minutes": 45
        },
        "car": {
            "id": 1,
            "plate_number": "ABC-123",
            "model_year": 2020,
            "color": "أبيض"
        },
        "address": {
            "id": 1,
            "address_name": "المنزل",
            "full_address": "شارع الملك فهد، الرياض"
        },
        "created_at": "2024-01-15T09:30:00Z",
        "updated_at": "2024-01-15T10:20:00Z"
    }
}
```

### Error Responses

```json
{
    "success": false,
    "message": "Order not found or cannot be cancelled",
    "data": null
}
```

---

## 7. Complete Order

### Endpoint

```
PATCH /orders/{id}/complete
```

### Description

Mark an order as completed. Only delegates can complete orders assigned to them.

### Authentication

Required (Delegate only)

### URL Parameters

| Parameter | Type    | Required | Description |
| --------- | ------- | -------- | ----------- |
| `id`      | integer | Yes      | Order ID    |

### Response

```json
{
    "success": true,
    "message": "Order completed successfully",
    "data": {
        "id": 1,
        "order_number": "ORD-2024-001",
        "status": "completed",
        "payment_status": "paid",
        "total_price": 75.0,
        "completed_at": "2024-01-15T11:30:00Z",
        "service": {
            "id": 1,
            "name": "غسيل خارجي وداخلي",
            "price": 50.0,
            "duration_minutes": 45
        },
        "car": {
            "id": 1,
            "plate_number": "ABC-123",
            "model_year": 2020,
            "color": "أبيض"
        },
        "address": {
            "id": 1,
            "address_name": "المنزل",
            "full_address": "شارع الملك فهد، الرياض"
        },
        "created_at": "2024-01-15T09:30:00Z",
        "updated_at": "2024-01-15T11:30:00Z"
    }
}
```

### Error Responses

```json
{
    "success": false,
    "message": "Order not found or cannot be completed",
    "data": null
}
```

---

## Business Logic & Calculations

### Price Calculation

The total price is calculated as follows:

1. **Service Price**: Base price from service or package
2. **Addons Price**: Sum of all selected addon services
3. **Subtotal**: Service Price + Addons Price
4. **Discount**: Applied based on coupon (percentage or fixed amount)
5. **Total Price**: Subtotal - Discount

### Example Calculation

```
Service Price: 50.00 SAR
Addons: [25.00, 15.00] = 40.00 SAR
Subtotal: 50.00 + 40.00 = 90.00 SAR
Coupon: 10% discount = 9.00 SAR
Total Price: 90.00 - 9.00 = 81.00 SAR
```

### Coupon Types

- **Percentage**: Discount is calculated as percentage of subtotal
- **Fixed**: Fixed amount discount (e.g., 10 SAR off)

### Wallet Payment

- Requires sufficient balance in user's wallet
- Amount is deducted immediately upon order creation
- Transaction record is created automatically

---

## Order Flow

### Customer Flow

1. **Create Order** → Status: `pending`
2. **Order Confirmed** → Status: `confirmed` (by admin)
3. **Delegate Assigned** → Delegate assigned to order
4. **Work Started** → Status: `in_progress`
5. **Work Completed** → Status: `completed` (by delegate)

### Delegate Flow

1. **Receive Assignment** → Order assigned to delegate
2. **Update Location** → Real-time location updates
3. **Start Work** → Update status to `in_progress`
4. **Complete Work** → Mark order as `completed`

### Cancellation Rules

- **Customer**: Can cancel `pending` orders
- **Delegate**: Can cancel `confirmed` or `in_progress` orders
- **Admin**: Can cancel any order
- **Time Limit**: Orders can be cancelled within 1 hour of booking

---

## Data Models

### Order Model

```json
{
    "id": 1,
    "order_number": "ORD-2024-001",
    "user_id": 1,
    "delegate_id": 2,
    "service_id": 1,
    "package_id": null,
    "car_id": 1,
    "address_id": 1,
    "coupon_id": 1,
    "booking_datetime": "2024-01-15T10:00:00Z",
    "estimated_start_time": "2024-01-15T10:30:00Z",
    "actual_start_time": "2024-01-15T10:35:00Z",
    "completed_at": "2024-01-15T11:30:00Z",
    "service_price": 50.0,
    "addons_price": 25.0,
    "discount_amount": 7.5,
    "total_price": 67.5,
    "payment_method": "wallet",
    "payment_status": "paid",
    "status": "completed",
    "notes": "Customer notes",
    "delegate_notes": "Delegate notes",
    "delegate_latitude": 24.7136,
    "delegate_longitude": 46.6753,
    "delegate_location_updated_at": "2024-01-15T10:15:00Z",
    "cancellation_reason": null,
    "created_at": "2024-01-15T09:30:00Z",
    "updated_at": "2024-01-15T11:30:00Z"
}
```
## Business Logic

### Address Management Rules

1. **First Address**: When a user creates their first address, it automatically becomes the default address.

2. **Default Address**: Only one address can be default per user. Setting a new address as default will remove the default status from other addresses.

3. **Delete Default**: When deleting the default address, if other addresses exist, the first available address will be set as default.

4. **User Isolation**: Users can only access, modify, or delete their own addresses.

5. **Phone Verification**: All address operations require phone verification.

### Car Management Rules

1. **First Car**: When a user creates their first car, it automatically becomes the default car.

2. **Default Car**: Only one car can be default per user. Setting a new car as default will remove the default status from other cars.

3. **Delete Default**: When deleting the default car, if other cars exist, the first available car will be set as default.

4. **User Isolation**: Users can only access, modify, or delete their own cars.

## Testing

You can test these endpoints using the provided test suites:

```bash
# Test Address endpoints
php artisan test --filter=AddressControllerTest

# Test Car endpoints
php artisan test --filter=CarsControllerTest

# Test all endpoints
php artisan test
```

## Rate Limiting

All endpoints are subject to rate limiting. Please implement appropriate rate limiting in your client applications.

## Authentication

All protected endpoints require a valid Bearer token in the Authorization header:
