- ```kotlin
  fun Request.getBody() =
      when (val response = executeRequest()) {
          is Success -> response.body
          is HttpError -> throw HttpException(response.status)
      }
  ```
-