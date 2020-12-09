# Об'єкт JumpListCategory

* `type` String (опціонально) - Один з наступних:
  * `tasks` - Items in this category will be placed into the standard `Tasks` category. There can be only one such category, and it will always be displayed at the bottom of the Jump List.
  * `frequent` - Відображає список файлів, що часто відкривалися додатком, назву та елементи встановлює Windows.
  * `recent` - Displays a list of files recently opened by the app, the name of the category and its items are set by Windows. Items may be added to this category indirectly using `app.addRecentDocument(path)`.
  * `custom` - Відображає задачі чи посилання на файли, `name` має бути визначене додатком.
* `name` String (optional) - Must be set if `type` is `custom`, otherwise it should be omitted.
* `items` JumpListItem[] (optional) - Array of [`JumpListItem`](jump-list-item.md) objects if `type` is `tasks` or `custom`, otherwise it should be omitted.

**Note:** If a `JumpListCategory` object has neither the `type` nor the `name` property set then its `type` is assumed to be `tasks`. If the `name` property is set but the `type` property is omitted then the `type` is assumed to be `custom`.
