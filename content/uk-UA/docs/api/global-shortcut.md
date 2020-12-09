# globalShortcut

> Виявляє клавіатурні події навіть якщо програма зараз не у фокусі.

Процес: [Main](../glossary.md#main-process)

Модуль `globalShortcut` може зареєструвати/скасувати реєстрацію глобального сполучення клавіш в операційній системі, тож ви можете налаштувати операції для різних сполучень клавіш.

**Note:** The shortcut is global; it will work even if the app does not have the keyboard focus. You should not use this module until the `ready` event of the app module is emitted.

```javascript
const {app, globalShortcut} = require('electron')

app.on('ready', () => {
  // Register a 'CommandOrControl+X' shortcut listener.
  const ret = globalShortcut.register('CommandOrControl+X', () => {
    console.log('CommandOrControl+X is pressed')
  })

  if (!ret) {
    console.log('registration failed')
  }

  // Check whether a shortcut is registered.
  console.log(globalShortcut.isRegistered('CommandOrControl+X'))
})

app.on('will-quit', () => {
  // Unregister a shortcut.
  globalShortcut.unregister('CommandOrControl+X')

  // Unregister all shortcuts.
  globalShortcut.unregisterAll()
})
```

## Методи

Модуль `GlobalShortcut` має такі методи:

### `globalShortcut.register(accelerator, callback)`

* `accelerator` [Accelerator](accelerator.md)
* `callback` Функція

Registers a global shortcut of `accelerator`. The `callback` is called when the registered shortcut is pressed by the user.

When the accelerator is already taken by other applications, this call will silently fail. This behavior is intended by operating systems, since they don't want applications to fight for global shortcuts.

### `globalShortcut.isRegistered(accelerator)`

* `accelerator` [Accelerator](accelerator.md)

Повертає `Boolean` - Якщо додаток має зареєстрований `accelerator`.

When the accelerator is already taken by other applications, this call will still return `false`. This behavior is intended by operating systems, since they don't want applications to fight for global shortcuts.

### `globalShortcut.unregister(accelerator)`

* `accelerator` [Accelerator](accelerator.md)

Скасовує реєстрацію глобального сполучення клавіш `accelerator`.

### `globalShortcut.unregisterAll()`

Скасовує реєстрацію всіх глобальних сполучень клавіш.
