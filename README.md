<h1 align="center">TL NTLM DIO</h1>

# About
Dart/Flutter NTLM Authentication as an interceptor for
[dio](https://pub.dev/packages/dio).

<br />

# Versions
## 1.0.0
- initial release

<br />

# Example

```dart
fetch() async {
  final baseOptions = BaseOptions();
  final credentials = Credentials(
    domain: 'domain',
    username: 'username',
    password: 'password'
  );

  Dio dio = Dio(baseOptions);

  final cookieJar = CookieJar();

  dio.interceptors.add(CookieManager(cookieJar));
  dio.interceptors.add(NtlmInterceptor(credentials, () =>
    Dio(baseOptions)..interceptors.add(CookieManager(cookieJar))
  ));

  final response = await dio.get(config.url);
}
```
