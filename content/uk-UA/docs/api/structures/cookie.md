# Об'єкт cookie

* `name` String - Ім'я кукі.
* `value` String - Значення куки.
* `domain` String (optional) - Домен куки.
* `hostOnly` Boolean (optional) - Чи кука буде host-only.
* `path` String (optional) - Шлях до куки.
* `secure` Boolean (optional) - Чи кука позначена як безпечна.
* `httpOnly` Boolean (optional) - Чи кука позначена як HTTP-only.
* `session` Boolean (optional) - Whether the cookie is a session cookie or a persistent cookie with an expiration date.
* `expirationDate` Double (optional) - The expiration date of the cookie as the number of seconds since the UNIX epoch. Not provided for session cookies.
