# Anbernic Console UI — RG556

Оригинальный Android launcher-проект по мотивам компоновки современной консольной панели.

## Что уже заложено
- 16:9 landscape UI для RG556
- навигация физическими кнопками Android/контроллера
- Home / My Games / Settings / Accounts
- локальный mock-аккаунт
- Developer Panel
- developer mode хранится только в RAM и поэтому скрывается после перезапуска процесса/устройства
- выбор APK для Add applications
- выбор APK для System update (передаётся Android Package Installer)
- HOME-категория в manifest, чтобы launcher можно было выбрать как домашний экран

## Firebase
Сейчас аккаунты локальные. Следующий слой рекомендуется сделать через:
`AccountRepository` -> `LocalAccountRepository` -> позднее `FirebaseAccountRepository`.

Это позволяет добавить Firebase Auth/Firestore без переписывания экранов.

## Сборка
Откройте проект в Android Studio с Android SDK 35 и соберите:
`app > Build > Build APK(s)`

Для публикации используйте собственный applicationId и подпись release-keystore.

## Важно для "System update"
Android не разрешает произвольному приложению обновлять само себя без обычного package installer/совместимой подписи. Для публичного релиза обновления должны быть подписаны тем же ключом, что и установленная версия.
