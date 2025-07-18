# Медицинское приложение (Flutter)

Мобильное приложение для анализа медицинских данных пациентов с заболеваниями щитовидной железы.

## Описание

Приложение позволяет:
- Загружать Excel файлы с анализами пациентов
- Автоматически анализировать отклонения от нормы
- Просматривать детальные отчеты
- Управлять нормами анализов (для администраторов)

## Технологии

- **Flutter** - фреймворк для мобильной разработки
- **Provider** - управление состоянием
- **HTTP** - работа с API
- **File Picker** - выбор файлов
- **Secure Storage** - безопасное хранение данных

## Требования

- Flutter SDK 3.0.0 или выше
- Dart SDK 3.0.0 или выше
- Android Studio / VS Code
- Android SDK (для Android)
- Xcode (для iOS)

## Установка

1. **Клонируйте репозиторий:**
   ```bash
   git clone <repository-url>
   cd medical_app
   ```

2. **Установите зависимости:**
   ```bash
   flutter pub get
   ```

3. **Настройте подключение к бэкенду:**
   
   Откройте файл `lib/providers/auth_provider.dart` и измените URL сервера:
   
   ```dart
   // Для Android эмулятора
   static const String _baseUrl = 'http://10.0.2.2:5000';
   
   // Для iOS симулятора
   // static const String _baseUrl = 'http://localhost:5000';
   
   // Для реального устройства (замените на IP вашего сервера)
   // static const String _baseUrl = 'http://192.168.1.100:5000';
   ```

## Запуск

### Android

1. **Подключите устройство или запустите эмулятор**

2. **Запустите приложение:**
   ```bash
   flutter run
   ```

### iOS

1. **Установите iOS зависимости:**
   ```bash
   cd ios
   pod install
   cd ..
   ```

2. **Запустите приложение:**
   ```bash
   flutter run
   ```

## Тестовые данные

Для входа в приложение используйте:

**Врач:**
- Логин: `doctor1`
- Пароль: `123456`

**Администратор:**
- Логин: `admin`
- Пароль: `123456`

## Структура проекта

```
lib/
├── main.dart              # Главный файл приложения
├── providers/             # Провайдеры состояния
│   ├── auth_provider.dart    # Аутентификация
│   ├── reports_provider.dart # Отчеты
│   └── norms_provider.dart   # Нормы анализов
└── screens/               # Экраны приложения
    ├── login_screen.dart     # Экран входа
    ├── home_screen.dart      # Главный экран
    ├── upload_screen.dart    # Загрузка файлов
    ├── reports_screen.dart   # Просмотр отчетов
    ├── profile_screen.dart   # Профиль пользователя
    └── admin_screen.dart     # Администрирование
```

## Функциональность

### Для врачей:
- Вход в систему
- Загрузка Excel файлов с анализами
- Просмотр отчетов
- Анализ отклонений от нормы

### Для администраторов:
- Все функции врача
- Управление нормами анализов
- Добавление/редактирование/удаление норм

## Формат файлов

Приложение поддерживает Excel файлы (.xlsx, .xls) со следующей структурой:

| Код пациента | Возраст | Щелочная фосфатаза | Кальций общий | ТТГ | Т4 свободный | ... |
|-------------|---------|-------------------|---------------|-----|--------------|-----|
| 001         | 45      | 88                | 3.21          | 0.85| 13.0         | ... |
| 002         | 56      | 59                | 3.00          | 0.87| 15.0         | ... |

## Анализируемые показатели

- Щелочная фосфатаза
- Кальций общий
- ТТГ (тиреотропный гормон)
- Т4 свободный
- Кальцитонин
- Паратгормон
- Антитела к тиреоглобулину
- РЭА (раково-эмбриональный антиген)

## Сборка релизной версии

### Android APK:
```bash
flutter build apk --release
```

### Android App Bundle:
```bash
flutter build appbundle --release
```

### iOS:
```bash
flutter build ios --release
```

## Устранение неполадок

### Ошибка подключения к серверу:
1. Убедитесь, что бэкенд запущен
2. Проверьте правильность URL в `auth_provider.dart`
3. Для реального устройства используйте IP адрес сервера

### Ошибки при загрузке файлов:
1. Убедитесь, что файл имеет правильный формат (.xlsx, .xls)
2. Проверьте структуру данных в файле
3. Убедитесь, что у пользователя есть права на загрузку

### Проблемы с правами доступа:
1. Войдите как администратор для управления нормами
2. Убедитесь, что токен не истек

## Лицензия

© 2024 Медицинская команда. Все права защищены. 