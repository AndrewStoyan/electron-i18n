# Об'єкт MemoryInfo

* `pid` Integer - Ідентифікатор процесу.
* `workingSetSize` Integer - Кількість пам'яті, що прив'язана до фактичної фізичної RAM в даний момент.
* `peakWorkingSetSize` Integer - The maximum amount of memory that has ever been pinned to actual physical RAM. On macOS its value will always be 0.
* `privateBytes` Integer - The amount of memory not shared by other processes, such as JS heap or HTML content.
* `sharedBytes` Integer - The amount of memory shared between processes, typically memory consumed by the Electron code itself

Зверніть увагу, що всі статистичні дані представлені в кілобайтах.
