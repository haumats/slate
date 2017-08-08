# AVAY Backend API
Development URL: [https://sapi.avay.vn]([https://sapi.avay.vn])

### Get all provinces: `[GET] /provinces`

* Request (application/json)
  - Method: `GET`
  - Route: `/provinces`
  - URL: `https://sapi.avay.vn/provinces`

* Response 200 (application/json)
  - Body
  ```javascript
  {
      "total": 3,
      "provinces_list": [
          "An Giang",
          "Bắc Giang",
          "Bắc Kạn"
      ]
  }
  ```javascript

### Get a new captcha: `[GET] /captcha`

* Request (application/json)
  - Method: `GET`
  - Route: `/captcha`
  - URL: `https://sapi.avay.vn/captcha`

* Response 200 (application/json)
  - Body
  ```javascript
    {
        "captcha_key": "Ha)jw9y*",
        "captcha_data": "<svg xmlns= ..."
    }
  ```javascript

### Create a new OTP: `[POST] /otps`

* Request (application/json)
  - Method: `POST`
  - Route: `/otps`
  - URL: `https://sapi.avay.vn/otps`
  - Headers:
  ```javascript
    Content-Type: "application/json"
  ```javascript
  - Body
  ```javascript
    {
        "captcha_key": "Ha)jw9y*",
        "captcha_text": "a2gs",
        "phone_number": "0987000001",
        "purpose": "check_offers",
        "fingerprint": "9ef724de80232fe17a9180a42a86bb43",
        "source": "android_app",
        "version": "20170704"
    }
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript    
    {
        "id": 6,
        "phone_number": "0987000001",
        "purpose": "check_offers",
        "expire_at": "2016-11-24T03:05:22.770Z"
    }
  ```javascript


### (Only for development) Get OTP (with code) by id: `[GET] /otps/:id`

* Request (application/json)
  - Method: `GET`
  - Route: `/otps/:id`
  - URL: `https://sapi.avay.vn/otps/6`
* Response 200 (application/json)
  - Body
  ```javascript
    {
        "id": 6,
        "phone_number": "0987000001",
        "code": "307672",
        "purpose": "check_offers",
        "is_verified": false,
        "expire_at": "2016-11-24T03:05:22.770Z",
        "created_at": "2016-11-24T02:50:22.770Z",
        "updated_at": "2016-11-24T02:50:22.770Z"
    }
  ```javascript


### Verify an OTP: `[POST] /otps/verify`

* Request (application/json)
  - Method: `POST`
  - Route: `/otps/verify`
  - URL: `https://sapi.avay.vn/otps/verify`
  - Headers:
  ```javascript
    Content-Type: "application/json"
  ```javascript
  - Body
  ```javascript
    {
        "id": 6,
        "phone_number": "0987000001",
        "code": "307672"
    }
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript    
    {
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJvdHBfaWQiOjYsInBob25lX251bWJlciI6IjA5ODcwMDAwMDEiLCJpYXQiOjE0Nzk5NTU5ODF9.ViAeetViVsJknWM0LKd3T01RFDX2dk6ebt8h1LVWLSM"
    }
  ```javascript


### Get list of all offers: `[GET] /offers/all`

* Request (application/json)
  - Method: `GET`
  - Route: `/offers/all`
  - URL: `https://sapi.avay.vn/offers/all`
* Response 200 (application/json)
  - Body
  ```javascript    
    {
        "total": 11,
        "offer_list": [
            {
              "id": 1,
              "code": "HC01",
              "bank_id": 1,
              "min_amount": 5000000,
              "max_amount": 25000000,
              "min_tenor": 1,
              "max_tenor": 6,
              "interest_rate": 59.99,
              "required_national_id": true,
              "required_family_book": false,
              "required_vehicle_document": true,
              "special_requirement": "",
              "bank": {
                "id": 1,
                "name": "Home Credit",
                "code": "home_credit_test",
                "logo": "home_credit.png"
              }
            },
            {
              "id": 2,
              "code": "HC02",
              "bank_id": 1,
              "min_amount": 10000000,
              "max_amount": 40000000,
              "min_tenor": 1,
              "max_tenor": 12,
              "interest_rate": 39.99,
              "required_national_id": false,
              "required_family_book": true,
              "required_vehicle_document": false,
              "special_requirement": "",
              "bank": {
                "id": 1,
                "name": "Home Credit",
                "code": "home_credit_test",
                "logo": "home_credit.png"
              }
            }
        ]
    }
  ```javascript


### Get list of qualified offers: `[GET] /offers`

* Request (application/json)
  - Method: `GET`
  - Route: `/offers`
  - URL: `https://sapi.avay.vn/offers`
  - Headers
  ```javascript
    Authorization: "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJvdHBfaWQiOjUsInBob25lX251bWJlciI6IjA5ODc2NTQzMjEiLCJpYXQiOjE0Nzk5NTU2NDB9.KyoddRCqC1Pr7IpR8ajHJ3OQ6z3T-tY_RauFH72jf-4.eyJvdHBfaWQiOjEsInBob25lX251bWJlciI6IjA5ODcwMDAwMDEiLCJpYXQiOjE0Nzk4ODAwMzl9.tjeyHOT6ik__F1_SxIA_94EBgmRmwR2FCKcHMKtH44U"
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript    
    {
        "total": 2,
        "offer_list": [
            {
                "id": 3,
                "min_amount": 20000000,
                "max_amount": 50000000,
                "min_tenor": 6,
                "max_tenor": 18,
                "interest_rate": 29.99,
                "required_national_id": true,
                "required_family_book": true,
                "required_vehicle_document": false,
                "special_requirement": "",
                "bank": {
                    "id": 1,
                    "name": "Home Credit",
                    "code": "home_credit",
                    "logo": "https://www.homecredit.vn/img/logo-hc2016-main.png"
                }
            },
            {
                "id": 4,
                "min_amount": 30000000,
                "max_amount": 100000000,
                "min_tenor": 6,
                "max_tenor": 18,
                "interest_rate": 19.99,
                "required_national_id": true,
                "required_family_book": true,
                "required_vehicle_document": true,
                "special_requirement": "Đối với khoản vay này, ngoài CMND và sổ hộ khẩu, bạn cần có đăng ký xe chính chủ (xe mới sử dụng dưới 30 tháng), hoặc sao kê bảng lương hay hợp đồng bảo hiểm.",
                "bank": {
                    "id": 2,
                    "name": "FE Credit",
                    "code": "fe_credit",
                    "logo": "https://fecredit.com.vn/wp-content/themes/fe-credit/assets/images/logo-vn.png"
                }
            }
        ],
        "telco": "viettel",
        "telco_score": 800
    }
  ```javascript
* Response 200 (application/json) for case user is having a loan within the last 90 days:
  - Body
  ```javascript
    {
        "total": 0,
        "offer_list": [],
        "total_disabled": 1,
        "disabled_offer_list": [
            {
                "id": 2,
                "min_amount": 10000000,
                "max_amount": 40000000,
                "min_tenor": 1,
                "max_tenor": 12,
                "interest_rate": 39.99,
                "required_national_id": true,
                "required_family_book": true,
                "required_vehicle_document": false,
                "special_requirement": "",
                "bank": {
                    "id": 1,
                    "name": "Home Credit",
                    "code": "home_credit_test",
                    "logo": "home_credit.png"
                }
            }
        ]
    }  
  ```javascript


### Get a specific offers: `[GET] /offers/:id`

* Request (application/json)
  - Method: `GET`
  - Route: `/offers/:id`
  - URL: `https://sapi.avay.vn/offers/4`
  - Headers
  ```javascript
    Authorization: "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJvdHBfaWQiOjUsInBob25lX251bWJlciI6IjA5ODc2NTQzMjEiLCJpYXQiOjE0Nzk5NTU2NDB9.KyoddRCqC1Pr7IpR8ajHJ3OQ6z3T-tY_RauFH72jf-4.eyJvdHBfaWQiOjEsInBob25lX251bWJlciI6IjA5ODcwMDAwMDEiLCJpYXQiOjE0Nzk4ODAwMzl9.tjeyHOT6ik__F1_SxIA_94EBgmRmwR2FCKcHMKtH44U"
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript
  {
      "id": 4,
      "min_amount": 30000000,
      "max_amount": 100000000,
      "min_tenor": 6,
      "max_tenor": 18,
      "interest_rate": 19.99,
      "required_national_id": true,
      "required_family_book": true,
      "required_vehicle_document": false,
      "special_requirement": "",
      "bank": {
          "id": 2,
          "name": "FE Credit",
          "code": "fe_credit_test",
          "logo": "fe_credit.png"
      }
  }
  ```javascript


### Create a new user: `[POST] /users`

* Request (application/json)
  - Method: `POST`
  - Route: `/users`
  - URL: `https://sapi.avay.vn/users`
  - Headers:
  ```javascript
    Content-Type: "application/json"
    Authorization: "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJvdHBfaWQiOjUsInBob25lX251bWJlciI6IjA5ODc2NTQzMjEiLCJpYXQiOjE0Nzk5NTU2NDB9.KyoddRCqC1Pr7IpR8ajHJ3OQ6z3T-tY_RauFH72jf-4.eyJvdHBfaWQiOjEsInBob25lX251bWJlciI6IjA5ODcwMDAwMDEiLCJpYXQiOjE0Nzk4ODAwMzl9.tjeyHOT6ik__F1_SxIA_94EBgmRmwR2FCKcHMKtH44U"
  ```javascript
  - Body:
  ```javascript
    {
        "password": "secret",
        "full_name": "Nguyễn Văn Tuấn",
        "national_id_number": "123456789",
        "monthly_income": 11000000,
        "province": "An Giang"
    }
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript
    {
        "id": 2,
        "phone_number": "0987000001",
        "full_name": "Nguyễn Văn Tuấn",
        "national_id_number": "123456789",
        "monthly_income": 11000000,
        "province": "An Giang"
    }
  ```javascript


### Search user by phone_number, national_id_number (optional): `[GET] /users`

* Request (application/json)
  - Method: `GET`
  - Route: `/users`
  - URL:
  ```javascript
    https://sapi.avay.vn/users?phone_number=0987000002
    or
    https://sapi.avay.vn/users?phone_number=0987000001&national_id_number=111111111
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript
    {
        "id": 3,
        "phone_number": "0987000002"
    }
    or
    {
        "id": 1,
        "phone_number": "0987000001",
        "national_id_number": "111111111"
    }    
  ```javascript

### Update user's information (full_name/national_id_number/monthly_income/province): `[PUT] /users/:user_id`

* Request (application/json)
  - Method: `PUT`
  - Route: `/users/:id`
  - URL: `https://sapi.avay.vn/users/1`
  - Headers:
  ```javascript
    Content-Type: "application/json"
    Authorization: "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJvdHBfaWQiOjUsInBob25lX251bWJlciI6IjA5ODc2NTQzMjEiLCJpYXQiOjE0Nzk5NTU2NDB9.KyoddRCqC1Pr7IpR8ajHJ3OQ6z3T-tY_RauFH72jf-4.eyJvdHBfaWQiOjEsInBob25lX251bWJlciI6IjA5ODcwMDAwMDEiLCJpYXQiOjE0Nzk4ODAwMzl9.tjeyHOT6ik__F1_SxIA_94EBgmRmwR2FCKcHMKtH44U"
  ```javascript
  - Body:
  ```javascript
    {
        "phone_number": "0987000001",
        "full_name": "Nguyễn Văn Tuấn",
        "national_id_number": "111111111",
        "monthly_income": 12000000,
        "province": "An Giang"
    }
  ```javascript

* Response 200 (application/json)
  - Body
  ```javascript
    {
        "id": 1,
        "phone_number": "0987000001",
        "full_name": "Nguyễn Văn Tuấn",
        "national_id_number": "111111111",
        "monthly_income": 12000000,
        "province": "An Giang"
    }
  ```javascript

### Update user's password: `[PUT] /users/:user_id/password`

* Request (application/json)
  - Method: `PUT`
  - Route: `/users/:id`
  - URL: `https://sapi.avay.vn/users/1/password`
  - Headers:
  ```javascript
    Content-Type: "application/json"
    Authorization: "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJvdHBfaWQiOjUsInBob25lX251bWJlciI6IjA5ODc2NTQzMjEiLCJpYXQiOjE0Nzk5NTU2NDB9.KyoddRCqC1Pr7IpR8ajHJ3OQ6z3T-tY_RauFH72jf-4.eyJvdHBfaWQiOjEsInBob25lX251bWJlciI6IjA5ODcwMDAwMDEiLCJpYXQiOjE0Nzk4ODAwMzl9.tjeyHOT6ik__F1_SxIA_94EBgmRmwR2FCKcHMKtH44U"
  ```javascript
  - Body:
  ```javascript
    {
        "phone_number": "0987000001",
        "national_id_number": "111111111",
        "password": "newpassword",
        "password_confirmation": "newpassword"
    }
  ```javascript

* Response 200 (application/json)
  - Body
  ```javascript
    {
        "id": 1,
        "phone_number": "0987000001",
    }
  ```javascript

### Login user to get token: `[POST] /users/login`

* Request (application/json)
  - Method: `POST`
  - Route: `/users/login`
  - URL: `https://sapi.avay.vn/users/login`
  - Headers:
  ```javascript
    Content-Type: "application/json"
  ```javascript
  - Body:
  ```javascript
    {
        "phone_number": "0987000001",
        "password": "password"
    }    
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript
    {
        "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAxIiwiaWF0IjoxNDgwMzA0MjAxLCJleHAiOjE0ODA5MDkwMDF9.1Ltn2_Tx9Ixu2Er_-xGumgJjkXBIYRSBTiZ_9wg7L8g",
        "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAxIiwiZnVsbF9uYW1lIjoiTmd1eeG7hW4gVsSDbiBUdeG6pW4iLCJuYXRpb25hbF9pZF9udW1iZXIiOiIxMTExMTExMTEiLCJtb250aGx5X2luY29tZSI6MTEwMDAwMDAsInByb3ZpbmNlIjoiSMOgIE7hu5lpIiwidG9rZW5fdHlwZSI6InJlZnJlc2giLCJpYXQiOjE0OTkxNjM4OTUsImV4cCI6MTUwMDQ1OTg5NX0.uLFQgqar5wsnu6kOhZ9ncHm_o9CYZZT9cNcMjjSGris"
    }
  ```javascript


### Refresh token when expired: `[POST] /users/refresh_token`

* Request (application/json)
  - Method: `POST`
  - Route: `/users/refresh_token`
  - URL: `https://sapi.avay.vn/users/refresh_token`
  - Headers:
  ```javascript
    Content-Type: "application/json"
    Authorization: "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAxIiwiZnVsbF9uYW1lIjoiTmd1eeG7hW4gVsSDbiBUdeG6pW4iLCJuYXRpb25hbF9pZF9udW1iZXIiOiIxMTExMTExMTEiLCJtb250aGx5X2luY29tZSI6MTEwMDAwMDAsInByb3ZpbmNlIjoiSMOgIE7hu5lpIiwidG9rZW5fdHlwZSI6InJlZnJlc2giLCJpYXQiOjE0OTkxNjM4OTUsImV4cCI6MTUwMDQ1OTg5NX0.uLFQgqar5wsnu6kOhZ9ncHm_o9CYZZT9cNcMjjSGris"
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript
  {
      "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAxIiwiZnVsbF9uYW1lIjoiTmd1eeG7hW4gVsSDbiBUdeG6pW4iLCJuYXRpb25hbF9pZF9udW1iZXIiOiIxMTExMTExMTEiLCJtb250aGx5X2luY29tZSI6MTEwMDAwMDAsInByb3ZpbmNlIjoiSMOgIE7hu5lpIiwiaWF0IjoxNDk5MTYzOTcxLCJleHAiOjE0OTk3Njg3NzF9.OQ5_wNmYfDK74WsjbUNkAyYvJcYjF3-k_f8JzPOK0sM",
      "refresh_token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAxIiwiZnVsbF9uYW1lIjoiTmd1eeG7hW4gVsSDbiBUdeG6pW4iLCJuYXRpb25hbF9pZF9udW1iZXIiOiIxMTExMTExMTEiLCJtb250aGx5X2luY29tZSI6MTEwMDAwMDAsInByb3ZpbmNlIjoiSMOgIE7hu5lpIiwidG9rZW5fdHlwZSI6InJlZnJlc2giLCJpYXQiOjE0OTkxNjM5NzEsImV4cCI6MTUwMDQ1OTk3MX0.0WIuv8R96tu7--47GQnFdqWtu7xe7ZTzekYIuxk5zRs"
  }
  ```javascript


### Delete a user: `[DELETE] /users/:user_id`
* Request (application/json)
  - Method: `DELETE`
  - Route: `/users/:user_id`
  - URL: `https://sapi.avay.vn/users/1?otp_id=11&code=000011`
  - Note: otp purpose should be 'delete_user'
  - Headers:
  ```javascript
    Authorization: "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjo1LCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDA1IiwibmF0aW9uYWxfaWRfbnVtYmVyIjoiNTU1NTU1NTU1IiwibW9udGhseV9pbmNvbWUiOjU1MDAwMDAwLCJpYXQiOjE0ODYxMTA0OTUsImV4cCI6MTQ4NjcxNTI5NX0.GhmNI4-UWwD_CzpYOvCV0GxvivaZYUxU-AlOWd--DWo"
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript
    {
        "message": "user is deleted"
    }
  ```javascript


### Create a new registration: `[POST] /registrations`

* Request (application/json)
  - Method: `POST`
  - Route: `/registrations`
  - URL: `https://sapi.avay.vn/registrations`
  - Headers:
  ```javascript
    Content-Type: "application/json"
    Authorization: "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAxIiwiaWF0IjoxNDgwMzA0MjAxLCJleHAiOjE0ODA5MDkwMDF9.1Ltn2_Tx9Ixu2Er_-xGumgJjkXBIYRSBTiZ_9wg7L8g"
  ```javascript
  - Body:
  ```javascript
    {}
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript
    {
        "id": 1,
        "user_id": 1,
        "status": "new",
        "created_at": "2017-06-07T01:32:19.187Z"
    }
  ```javascript


### Get a specific registration: `[GET] /registrations/:id`

* Request (application/json)
  - Method: `GET`
  - Route: `/registrations/:id`
  - URL: `https://sapi.avay.vn/registrations/1`
  - Headers
  ```javascript
    Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAxIiwiaWF0IjoxNDgxNjM0NDA5LCJleHAiOjE0ODIyMzkyMDl9.H0FYRLmeBR6K9_fZ_IogqbEA4gBjxwN4rjrgnkOlYKs
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript
    {
        "id": 5,
        "user_id": 282,
        "offer_id": 2,
        "loan_id": 273,
        "status": "success",
        "created_at": "2017-06-13T13:51:28.312Z",
        "offer": {
            "id": 2,
            "code": "HC02",
            "bank_id": 1,
            "bank": {
              "id": 1,
              "name": "Home Credit",
              "code": "home_credit_test",
              "logo": "home_credit.png"
            },
            "min_amount": 10000000,
            "max_amount": 40000000,
            "min_tenor": 1,
            "max_tenor": 12,
            "interest_rate": 39.99,
            "required_national_id": false,
            "required_family_book": true,
            "required_vehicle_document": false,
            "special_requirement": ""
        },
        "appointments":
           [ { "date": "2017-07-24",
               "times":
                [ { "begin": 13, "end": 14 },
                  { "begin": 14, "end": 15 },
                  { "begin": 15, "end": 16 },
                  { "begin": 16, "end": 17 }
                 ]
             },
             { "date": "2017-07-25",
               "times":
                [ { "begin": 8, "end": 9 },
                  { "begin": 9, "end": 10 },
                  { "begin": 10, "end": 11 },
                  { "begin": 11, "end": 12 },
                  { "begin": 13, "end": 14 },
                  { "begin": 14, "end": 15 },
                  { "begin": 15, "end": 16 },
                  { "begin": 16, "end": 17 } ] },
             { "date": "2017-07-26",
               "times":
                [ { "begin": 8, "end": 9 },
                  { "begin": 9, "end": 10 },
                  { "begin": 10, "end": 11 } ] }
            ]
    }
  ```javascript


### Get recent registration: `[GET] /registrations/recent`

* Request (application/json)
  - Method: `GET`
  - Route: `/registrations/recent`
  - URL: `https://sapi.avay.vn/registrations/recent`
  - Headers
  ```javascript
    Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAxIiwiaWF0IjoxNDgxNjM0NDA5LCJleHAiOjE0ODIyMzkyMDl9.H0FYRLmeBR6K9_fZ_IogqbEA4gBjxwN4rjrgnkOlYKs
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript
    {
        "id": 5,
        "user_id": 282,
        "offer_id": 2,
        "loan_id": 273,
        "status": "success",
        "created_at": "2017-06-13T13:51:28.312Z",
        "offer": {
            "id": 2,
            "code": "HC02",
            "bank_id": 1,
            "bank": {
              "id": 1,
              "name": "Home Credit",
              "code": "home_credit_test",
              "logo": "home_credit.png"
            },            
            "min_amount": 10000000,
            "max_amount": 40000000,
            "min_tenor": 1,
            "max_tenor": 12,
            "interest_rate": 39.99,
            "required_national_id": false,
            "required_family_book": true,
            "required_vehicle_document": false,
            "special_requirement": ""
        }
    }
  ```javascript


### Create a new loan: `[POST] /loans`

* Request (application/json)
  - Method: `POST`
  - Route: `/loans`
  - URL: `https://sapi.avay.vn/loans`
  - Headers:
  ```javascript
    Content-Type: "application/json"
    Authorization: "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAxIiwiaWF0IjoxNDgwMzA0MjAxLCJleHAiOjE0ODA5MDkwMDF9.1Ltn2_Tx9Ixu2Er_-xGumgJjkXBIYRSBTiZ_9wg7L8g"
  ```javascript
  - Body:
  ```javascript
    {
        "offer_id": 4,
        "desired_amount": 50000000,
        "desired_tenor": 12,
        "full_name": "Nguyễn Văn Tuấn",
        "national_id_number": "111111111",
        "monthly_income": 11000000,
        "province": "An Giang",
    }
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript
    {
        "id": 3,
        "user_id": 1,
        "offer_id": 4,
        "full_name": "Nguyễn Văn Tuấn",
        "national_id_number": "111111111",
        "monthly_income": 11000000,
        "province": "An Giang",
        "desired_amount": 50000000,
        "desired_tenor": 12,
        "status": "new",
        "is_locked": false
    }
  ```javascript


### Get list of loans: `[GET] /loans`

* Request (application/json)
  - Method: `GET`
  - Route: `/loans`
  - URL: `https://sapi.avay.vn/loans`
  - Headers
  ```javascript
    Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAxIiwiaWF0IjoxNDgxNjM0NDA5LCJleHAiOjE0ODIyMzkyMDl9.H0FYRLmeBR6K9_fZ_IogqbEA4gBjxwN4rjrgnkOlYKs
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript    
    {
        "total": 2,
        "loan_list": [
            {
                "id": 1,
                "user_id": 1,
                "full_name": "Nguyễn Văn Tuấn",
                "national_id_number": "111111111",
                "monthly_income": 11000000,
                "province": "An Giang",
                "desired_amount": 40000000,
                "desired_tenor": 15,
                "status": "new",
                "is_locked": false,
                "appointment": {
                    "date": "2017-07-20",
                    "time": {
                        "begin": 9,
                        "end": 10
                    }
                },
                "offer": {
                    "id": 3,
                    "min_amount": 20000000,
                    "max_amount": 50000000,
                    "min_tenor": 6,
                    "max_tenor": 18,
                    "interest_rate": 29.99,
                    "required_national_id": true,
                    "required_family_book": false,
                    "required_vehicle_document": true,
                    "special_requirement": "",
                    "bank": {
                        "id": 1,
                        "name": "Home Credit",
                        "code": "home_credit",
                        "logo": "home_credit.png"
                    }
                }
            },
            {
                "id": 3,
                "user_id": 1,
                "full_name": "Nguyễn Văn Tuấn",
                "national_id_number": "111111111",
                "monthly_income": 11000000,
                "province": "An Giang",
                "desired_amount": 50000000,
                "desired_tenor": 12,
                "status": "new",
                "is_locked": false,
                "appointment": "2017-07-24 13h-14h",
                "offer": {
                    "id": 4,
                    "min_amount": 30000000,
                    "max_amount": 100000000,
                    "min_tenor": 6,
                    "max_tenor": 18,
                    "interest_rate": 19.99,
                    "required_national_id": true,
                    "required_family_book": false,
                    "required_vehicle_document": true,
                    "special_requirement": "",
                    "bank": {
                        "id": 2,
                        "name": "FE Credit",
                        "code": "fe_credit",
                        "logo": "fe_credit.png"
                    }
                }
            }
        ]
    }
  ```javascript


### Get a specific loan: `[GET] /loans/:id`

* Request (application/json)
  - Method: `GET`
  - Route: `/loans/:id`
  - URL: `https://sapi.avay.vn/loans/2`
  - Query: `https://sapi.avay.vn/loans/2?without_related_data=true` if you don't want to get information about offer
  - Headers
  ```javascript
    Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAxIiwiaWF0IjoxNDgxNjM0NDA5LCJleHAiOjE0ODIyMzkyMDl9.H0FYRLmeBR6K9_fZ_IogqbEA4gBjxwN4rjrgnkOlYKs
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript
    {
        "id": 2,
        "user_id": 4,
        "full_name": "Nguyễn Văn Tuấn",
        "national_id_number": "444444444444",
        "monthly_income": 44000000,
        "province": "An Giang",
        "desired_amount": 32000000,
        "desired_tenor": 18,
        "status": "new",
        "is_locked": true,
        "created_at": "2017-02-06T09:36:35.825Z",
        "appointment": "2017-07-24 13h-14h",
        "offer": {
            "id": 5,
            "min_amount": 5000000,
            "max_amount": 35000000,
            "min_tenor": 1,
            "max_tenor": 18,
            "interest_rate": 29.99,
            "required_national_id": true,
            "required_family_book": false,
            "required_vehicle_document": true,
            "special_requirement": "",
            "bank": {
                "id": 2,
                "name": "FE Credit",
                "code": "fe_credit_test",
                "logo": "fe_credit.png"
            }
        }
    }  
  ```javascript
### update loan's appointment: `[PUT] /loans/:id/appointment`

* Request (application/json)
  - Method: `PUT`
  - Route: `/loans/:id/appointment`
  - URL: `https://sapi.avay.vn/loans/8/appointment`
  - Headers:
  ```javascript
    Content-Type: "application/json"
    Authorization: "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAxIiwiaWF0IjoxNDgwMzA0MjAxLCJleHAiOjE0ODA5MDkwMDF9.1Ltn2_Tx9Ixu2Er_-xGumgJjkXBIYRSBTiZ_9wg7L8g"
  ```javascript
  - Body:
  ```javascript
    {
      "date": "2017-07-24",
      "time": {
        "begin": 13,
        "end": 14
      }
    }
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript
    {
      "id": 8,
      "user_id": 1,
      "offer_id": 10,
      "full_name": "Nguyễn Văn Tuấn",
      "national_id_number": "777777777777",
      "monthly_income": 7777777,
      "province": "Lạng Sơn",
      "desired_amount": 100000000,
      "desired_tenor": 16,
      "status": "new",
      "is_locked": false,
      "created_at": "2017-07-24T04:19:20.000Z",
      "updated_at": "2017-07-26T03:54:06.442Z",
      "phone_number": "0987000006",
      "appointment": "2017-07-24 13h-14h",
      "offer": {
        "id": 10,
        "code": "FE07",
        "bank_id": 3,
        "min_amount": 200000000,
        "max_amount": 300000000,
        "min_tenor": 24,
        "max_tenor": 36,
        "interest_rate": 15.99,
        "required_national_id": true,
        "required_family_book": true,
        "required_vehicle_document": true,
        "special_requirement": "Đối với khoản vay này, ngoài CMND và sổ hộ khẩu, bạn cần có đăng ký xe chính chủ (xe mới sử dụng dưới 30 tháng), hoặc sao kê bảng lương hay hợp đồng bảo hiểm.",
        "created_at": "2017-07-26T03:53:36.443Z",
        "bank": {
          "id": 3,
          "name": "FE Credit",
          "code": "fe_credit",
          "logo": "fe_credit.png"
        }
      }
    }
  ```javascript

### Upload a document: `[POST] /documents`
* Request (application/json)
  - Method: `POST`
  - Route: `/documents`
  - URL: `https://sapi.avay.vn/documents`
  - Headers:
  ```javascript
    Authorization: "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAxIiwiaWF0IjoxNDgwMzA0MjAxLCJleHAiOjE0ODA5MDkwMDF9.1Ltn2_Tx9Ixu2Er_-xGumgJjkXBIYRSBTiZ_9wg7L8g"
  ```javascript
  - Body:
  ```javascript
    Form:
    {
        "category": "national_id_card",
        "code": "back_side",
        "name": "Mặt sau",
        "image": File("./cmnd.png")
    }
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript
    {
        "id": 3,
        "user_id": 2,
        "category": "national_id_card",
        "code": "back_side",
        "name": "Mặt sau",
        "image": "national_id_card_back_side_1480759049414.png"
    }  
  ```javascript


### Get list of documents of a user: `[GET] /documents`

* Request (application/json)
  - Method: `GET`
  - Route: `/documents`
  - URL: `https://sapi.avay.vn/documents`
  - Headers
  ```javascript
    Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoyLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAyIiwiaWF0IjoxNDgwNjc1Njc1LCJleHAiOjE0ODEyODA0NzV9.LmRcJyKj7clPxT22p0f0J_c01mFOWpTPDbW21ANH330
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript    
    {
        "total": 1,
        "document_list": [
            {
                "id": 1,
                "user_id": 2,
                "category": "family_book",
                "code": "page_1",
                "name": "Trang 1",
                "image": "family_book_page_1_1480669766550.png"
            }
        ]
    }
  ```javascript


### Get image of a document: `[GET] /documents/image/:filename`

* Request (application/json)
  - Method: `GET`
  - Route: `/documents/image/:filename`
  - URL: `https://sapi.avay.vn/documents/image/family_book_page_1_1480669766550.png`
  - Headers
  ```javascript
    Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoyLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAyIiwiaWF0IjoxNDgwNjc1Njc1LCJleHAiOjE0ODEyODA0NzV9.LmRcJyKj7clPxT22p0f0J_c01mFOWpTPDbW21ANH330
  ```javascript
* Response 200 (image/png)
  - Body: the image


### Delete a document: `[DELETE] /documents/:id`
* Request (application/json)
  - Method: `DELETE`
  - Route: `/documents/:id`
  - URL: `https://sapi.avay.vn/documents/3`
  - Headers:
  ```javascript
    Authorization: "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoyLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAyIiwiaWF0IjoxNDgwNjc1Njc1LCJleHAiOjE0ODEyODA0NzV9.LmRcJyKj7clPxT22p0f0J_c01mFOWpTPDbW21ANH330"
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript
    {
        "message": "document is deleted"
    }
  ```javascript


### Create a new attachment: `[POST] /attachments`

* Request (application/json)
  - Method: `POST`
  - Route: `/attachments`
  - URL: `https://sapi.avay.vn/attachments`
  - Headers:
  ```javascript
    Content-Type: "application/json"
    Authorization: "Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAxIiwiaWF0IjoxNDgxNjM0NDA5LCJleHAiOjE0ODIyMzkyMDl9.H0FYRLmeBR6K9_fZ_IogqbEA4gBjxwN4rjrgnkOlYKs"
  ```javascript
  - Body:
  ```javascript
    {
        "loan_id": 1,
        "document_id": 5
    }  
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript
    {
        "id": 3,
        "loan_id": 1,
        "document_id": 5
    }  
  ```javascript


### Get list of attachments: `[GET] /attachments`

* Request (application/json)
  - Method: `GET`
  - Route: `/attachments`
  - URL: `https://sapi.avay.vn/attachments?loan_id=1`
  - Headers
  ```javascript
    Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAxIiwiaWF0IjoxNDgxNjM0NDA5LCJleHAiOjE0ODIyMzkyMDl9.H0FYRLmeBR6K9_fZ_IogqbEA4gBjxwN4rjrgnkOlYKs
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript    
    {
        "total": 2,
        "attachment_list": [
            {
                "id": 1,
                "loan_id": 1,
                "document": {
                    "id": 3,
                    "user_id": 1,
                    "category": "national_id_card",
                    "code": "back_side",
                    "name": "Mặt sau",
                    "image": "national_id_card_back_side_1480669766970.png",
                    "is_active": true
                }
            },
            {
                "id": 2,
                "loan_id": 1,
                "document": {
                    "id": 4,
                    "user_id": 1,
                    "category": "national_id_card",
                    "code": "front_side",
                    "name": "Mặt trước",
                    "image": "national_id_card_front_side_1480669768999.png",
                    "is_active": false
                }
            }
        ]
    }
  ```javascript


### Create new device data: `[POST] /device_data` or anonymously `[POST] /device_data/anonymous`

* Request (application/json)
  - Method: `POST`
  - Route: `/device_data` or `[POST] /device_data/anonymous`
  - URL: `https://sapi.avay.vn/device_data`
  - Headers: (don't need authorization token for anonymous data)
  ```javascript
    Content-Type: "application/json"
    Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAxIiwiaWF0IjoxNDgxNjM0NDA5LCJleHAiOjE0ODIyMzkyMDl9.H0FYRLmeBR6K9_fZ_IogqbEA4gBjxwN4rjrgnkOlYKs    
  ```javascript
  - Body
  ```javascript
    {
        "imei": "12345678901234",
        "imei2": "001002003004005",
        "android_id": "a223kaj2jalci2",
        "device_id": "59b604f4d445842deefd999cdfa59e3b",
        "device_code": "iphone_7_plus",
        "device_os": "ios_10",
        "data_type": "location",
        "file": "test/call_log.csv"
    }
  ```javascript
* Response 200 (application/json)
  - Body
  ```javascript    
    {
        "id": 1,
        "user_id": 1,
        "imei": "12345678901234",
        "imei2": "001002003004005",
        "android_id": "a223kaj2jalci2",
        "device_id": "59b604f4d445842deefd999cdfa59e3b",        
        "device_code": "iphone_7_plus",
        "device_os": "ios_10",
        "data_type": "location",
        "data": "{}",
        "file": "iphone_7_plus_ios_10_location_a90af961d5f04adecd2e8cc4d6ec848d"
    }
  ```javascript
  ### Create new device data upload url: `[POST] /device_data/upload_url` or anonymously `[POST] /device_data/anonymous/upload_url`

* Request (application/json)
  - Method: `POST`
  - Route: `/device_data/upload_url` or `[POST] /device_data/anonymous/upload_url`
  - URL: `https://sapi.avay.vn/device_data/upload_url`
  - Headers: (don't need authorization token for anonymous data)
  ```
    Content-Type: "application/json"
    Authorization: Bearer eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VyX2lkIjoxLCJwaG9uZV9udW1iZXIiOiIwOTg3MDAwMDAxIiwiaWF0IjoxNDgxNjM0NDA5LCJleHAiOjE0ODIyMzkyMDl9.H0FYRLmeBR6K9_fZ_IogqbEA4gBjxwN4rjrgnkOlYKs    
  ```
  - Body: (require sign for anonymous data)
  ```
    { 
      "imei": "12345678901234",
      "imei2": "001002003004005",
      "android_id": "a223kaj2jalci2",
      "device_id": "59b604f4d445842deefd999cdfa59e3b",
       "device_code": "iphone_7_plus",
       "device_os": "ios_10",
       "data_type": "location",
       "file": "test/call_log.csv",
       "sign": "dskadladkakjsdaoieq" (optional)
    }
  ```
  - Sign build: "[data\_type]\_[device\_id]\_[device\_os]\_[timestamp]", method: hash sha256 with secret key
* Response 200 (application/json)
  - Body
  ```    
    {
        "filename": "test.csv.gz",
        "url": "001002003004005",
        "upload_id": "a223kaj2jalci2",
        "expire_date": ""
    }
  ```
  * Request (application/json)
  - Method: `GET`
  - Route: `/device_data/retry/:upload_id`
  - URL: `https://sapi.avay.vn/device_data/retry/:upload_id`
  ```
    Content-Type: "application/json"
  ```
* Response 200 (application/json)
  - Body
  ```    
    {
        "filename": "test.csv.gz",
        "url": "001002003004005",
        "upload_id": "a223kaj2jalci2",
        "expire_date": ""
    }
  ```
