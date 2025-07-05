# Архитектура Frontend (Flutter)

## 1. Пакетная структура

![image](https://github.com/user-attachments/assets/72a76e3e-98a3-471c-986c-ae1e1a481470)


## 2. State Management

Riverpod (рекомендуется) для глобальных и локальных состояний.

Каждый feature имеет свой ChangeNotifier/StateNotifier.

Async-операции через FutureProvider и StreamProvider для подписок на WebSocket (чат).

## 3. Навигация

Использовать go_router:

Nested routing для разделения секций (Auth, Main).

Переадресация неавторизованных пользователей на экраны входа.

Параметры маршрутов для деталей (/services/:id).

## 4. Сетевые запросы

Dio + Retrofit для генерации API-клиента.

Интерцепторы:

JWT-токен (refresh).

Логирование запросов.

Обработка ошибок (401 → редирект на логин).

## 5. Реализация фич

Auth

Регистрация/вход через JWT, OAuth (Google SignIn)

Хранение токенов через flutter_secure_storage.

Marketplace

Фильтры (тип визы, цена, рейтинг).

Pagination (infinite scroll).

Детали услуги: портрет провайдера, отзывы, календарь доступности.

Order & Payments

Интеграция Stripe SDK (Native iOS/Android)

Выбор времени через TableCalendar.

Webhook-подписка через backend для статуса платежа.

Calendar & Tasks

syncfusion_flutter_calendar для Gantt и календаря.

Локальное кеширование задач (Hive) для оффлайн.

AI Assistant

Чат с OpenAI через WebSocket/REST.

Загрузка письма и отображение рекомендаций.

Голосовая симуляция: запись через flutter_sound, отправка на Whisper API.

Chat & Social

Реализация через WebSocket (Socket.IO или Django Channels).

Отдельный ChatNotifier с подпиской на потоки сообщений.

Notifications

Push (FCM) через firebase_messaging.

Локальные напоминания (flutter_local_notifications).

## 6. CI/CD и тестирование

GitHub Actions:

Анализ кода (Dart Analyze).

Unit-тесты и widget-тесты.

Сборка артефактов (APK, IPA).

E2E: integration_test с эмуляцией авторизации и основных сценариев.

## 7. Локализация

Использовать flutter_localizations и intl.

Структура ARB-файлов: lib/l10n/intl_en.arb, intl_ru.arb.

Эта архитектура позволит масштабировать приложение, разделять ответственность по модулям и интегрировать все backend-сервисы.

