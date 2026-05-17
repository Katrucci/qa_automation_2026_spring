# Jenkins CI/CD Configuration & Test Specification
**Версия Jenkins:** `2.541.3`

## Обзор
Данный документ представляет собой набор **User Stories**, разработанных специально для **написания автотестов** в Jenkins `2.541.3`. Каждый файл содержит чёткие acceptance criteria, предусловия (preconditions), пошаговые UI-сценарии и правила валидации. Это позволяет QA-инженерам и разработчикам автотестов быстро формировать тест-кейсы, проверять корректность интерфейса и автоматизировать проверку функциональности Jenkins.

Материал охватывает ключевые области: создание и настройку проектов, управление доступом (RBAC), конфигурацию сборок, параметры безопасности и кастомизацию Dashboard. Все сценарии структурированы так, чтобы их можно было напрямую переносить в автоматизированный фреймворк Selenium.

---

##  Ключевые функции и покрытие

###  Управление проектами и элементами (Item Management)

#### Создание новых элементов (New Item)
- Доступные типы элементов при создании через `New Item`:
    - `Pipeline`
    - `Freestyle project`
    - `Multi-configuration project`
    - `Folder`
    - `Multibranch Pipeline`
    - `Organization Folder`
- Требования к имени элемента: уникальное, алфавитно-цифровое, допускаются дефис и подчёркивание (без пробелов и спецсимволов).
- Кнопка `OK` становится активной только после ввода валидного имени и выбора типа элемента.
- Возврат на `Dashboard` без создания: клик по логотипу `Jenkins` в левом верхнем углу.

#### Multi-configuration Project
- **Enable/Disable проекта**: переключатель в правом верхнем углу страницы конфигурации. При отключении отображается сообщение `This project is currently disabled` с кнопкой `Enable`.
- **Source Code Management**:
    - Поддержка `Git` с настройками:
        - `Repository URL` (HTTPS, SSH, git://, локальный путь)
        - `Credentials`: `Username with password`, `GitHub App`, `SSH Username with private key`, `Secret file`, `Secret text`, `Certificate`
        - `Advanced`: `Name`, `Refspec`, добавление нескольких репозиториев
        - `Branches to build`: `Branch Specifier` с поддержкой `*/master`, `refs/heads/*`, переменных окружения, wildcard и регексов
        - `Repository browser`: интеграция с `githubweb`, `gitlab`, `bitbucketweb`, `FishEye` и др.
        - `Additional Behaviours`: `Advanced checkout behaviours`, `Clean after checkout`, `Merge before build`, `Prune stale remote-tracking branches` и более 20 других опций.

#### Pipeline Configuration > Advanced
- Кнопка `Advanced` (иконка гаечного ключа) открывает дополнительные настройки:
    - `Quiet period`: задержка в секундах перед запуском сборки (по умолчанию 5 сек)
    - `Display Name`: дружественное имя проекта для отображения в интерфейсе (если пусто — используется системное имя)

#### Multibranch Pipeline
- Автоматическое обнаружение и сборка веток из Git-репозитория.
- **Health metrics**:
    - Доступные метрики через кнопку `Add`:
        - `Child item with the given name`
        - `Child item with worst health` (с опцией `Recursive` по умолчанию)
        - `Health of the primary branch of a repository`
    - Кнопка `Add metrics` деактивируется после выбора всех трёх метрик.

#### Organization Folder
- **Scan Organization Folder Triggers**:
    - Опция `Periodically if not otherwise run` включена по умолчанию.
    - `Interval`: выбор интервала от `1 minute` до `4 weeks` для периодического сканирования организации на предмет изменений.

---

###  Безопасность и управление доступом (RBAC)

#### Manage Jenkins > Security
- **Authentication**:
    - Чекбокс `Keep me signed in` для управления сессией.
- **Security Realm** (источник аутентификации):
    - `Jenkins' own user database` (по умолчанию)
    - `Delegate to servlet container`
    - `GitHub Authentication Plugin`
    - `LDAP`
    - `None`
- **Allow users to sign up**: включение саморегистрации пользователей.
- **Authorization** (стратегии авторизации):
    - `Logged-in users can do anything` (по умолчанию)
    - `Anyone can do anything`
    - `GitHub Committer Authorization Strategy`
    - `Legacy mode`
    - `Matrix-based security`
    - `Project-based Matrix Authorization Strategy`
- **Allow anonymous read access**: доступ для неаутентифицированных пользователей в режиме "только чтение".
- **Markup Formatter**: `Plain text` (по умолчанию) или `Safe HTML`.
- **Agents**: режим TCP-порта для inbound-агентов — `Fixed`, `Random`, `Disable` (по умолчанию).
- **CSRF Protection**: `Default Crumb Issuer` + опция `Proxy Compatibility`.
- **Git plugin notifyCommit access tokens**: управление токенами для аутентификации запросов к `notifyCommit`.
- **Git Hooks**: опции `Allow on Controller` / `Allow on Agents` (рекомендуется отключать).
- **Hidden security warnings**: возможность скрыть отдельные предупреждения безопасности.
- **API Token**:
    - Управление генерацией `legacy API token` (не рекомендуется)
    - Включение статистики использования токенов (включено по умолчанию)
- **Content Security Policy**: включение/отключение `Enforce Content Security Policy`.
- **Git Host Key Verification Configuration**:
    - `Known hosts file` (по умолчанию)
    - `Accept first connection`
    - `Manually provided keys`
    - `No verification` (не рекомендуется)
- **Sandbox Configuration**: глобальное принудительное использование `Groovy Sandbox`.

#### Ролевая модель (Role-Based Authorization Strategy)
- Требуется установка плагина `Role-based Authorization Strategy`.
- **Глобальные роли (Global roles)**:
    - `admin`: `Overall/Administer`
    - `role_developer`: `Overall/Read`, `Job/Create`, `Job/Discover`, `View/Create`, `View/Read`
    - `role_viewer`: `Overall/Read`
- **Роли элементов (Item roles)** с паттерном `.*`:
    - `developer-project`: `Job/Build`, `Job/Cancel`, `Job/Configure`, `Job/Read`, `Job/Workspace`, `Run/Delete`, `Run/Update`
    - `viewer-project`: `Job/Read`
- **Поведение интерфейса по ролям**:

  | Роль | `New Item` | `Manage Jenkins` | `Welcome Dashboard` |
  |------|------------|------------------|-------------------|
  | Admin | Yes        | Yes              | `Create a job`, `Set up an agent`, `Configure a cloud`, `Learn more...` |
  | Developer | Yes        | ❌                | Только `Create a job` |
  | Viewer | ❌          | ❌                | Только просмотр существующих задач (без кнопок действий) |

---

###  Управление сборками и параметрами

#### Freestyle Project > General Settings
- **Discard old builds** (политика хранения):
    - `Strategy`: `Log rotation` (по умолчанию)
    - `Days to keep builds`, `Max # of builds to keep`
    - `Advanced`: `Days to keep artifacts`, `Max # of builds to keep with artifacts`, `Remove last build`
- **GitHub project**: `Project url`, `Display name` для статуса коммитов.
- **This project is parameterized** — доступные типы параметров:
  | Тип параметра | Ключевые поля |
  |--------------|-------------|
  | `Boolean parameter` | `Name`, `Default value`, `Description` |
  | `Choice parameter` | `Name`, `Choices` (по одному в строке), `Description` |
  | `Credentials parameter` | `Name`, `Credential type`, `Required`, `Default Value`, `Description` |
  | `File parameter` | `File Location`, `Description` (загрузка опциональна) |
  | `Multi-line string parameter` | `Name`, `Default Value`, `Description` |
  | `Password parameter` | `Name`, `Default Value`, `Description` |
  | `Run parameter` | `Name`, `Project`, `Filter` (`All Builds`, `Completed`, `Successful`, `Stable`), `Description` |
  | `String parameter` | `Name`, `Default Value`, `Description`, `Trim the string` |
- **Throttle builds**: ограничение частоты сборок (`Number of builds` + `Time period`), опция пропуска лимита для ручных запусков.
- **Execute concurrent builds if necessary**: разрешение параллельных сборок (с отдельными `workspace@N`).
- **Advanced**:
    - `Quiet period`, `Retry Count`, блокировка при сборке `upstream`/`downstream` проектов
    - `Use custom workspace` с указанием пути
    - `Keep the build logs of dependencies`, `Display Name`

---

###  Интерфейс и кастомизация Dashboard

#### Build History > Empty State
- При отсутствии сборок отображается пустая таблица с заголовками: `S`, `Build`, `Time since`, `Status`.
- Доступно переключение размера иконок: `S` / `M` / `L`.

#### Customize Displayed Columns in List View
- Через `Edit View` (иконка шестерёнки) доступны колонки:
    - `Status`, `Weather`, `Name`, `Last Success`, `Last Failure`, `Last Duration`, `Build Button`
- Управление колонками:
    - Добавление через `Add Column` dropdown
    - Удаление через иконку `×`
    - Изменение порядка через drag & drop (`≡`)
- Предупреждение о несохранённых изменениях при попытке уйти со страницы:  
  `Закрыть сайт? Изменения могут не сохраниться.` с кнопками `Выход` / `Отмена`.

---

##  Быстрый старт для QA / Автоматизации

1. **Разверните Jenkins** `2.541.3` и войдите под учётной записью `admin`.
2. **Подготовьте окружение для тестов**:  
   Установите плагин `Role-based Authorization Strategy`, включите `Role-Based Strategy` в `Manage Jenkins → Security → Authorization`.
3. **Создайте тестовых пользователей**:  
   `test_developer` и `test_viewer` с соответствующими правами (см. таблицу ролей выше).
4. **Запустите автотесты**:  
   Используйте acceptance criteria из файлов `US_XX.XXX.md` как готовые тест-кейсы. Все UI-элементы, локаторы и состояния кнопок описаны в формате, готовом для параметризации в Selenium/Playwright/Cypress.
5. **Валидация UI/UX**:  
   Проверяйте поведение `Edit View`, `Build History`, `Advanced` toggles и предупреждения о несохранённых изменениях согласно описанным сценариям.

---

##  Структура документации

Файлы названы по идентификаторам User Stories (`US_XX.XXX.md`). Каждый документ содержит:
- Чёткие acceptance criteria (готовые к маппингу на Asserts в тестах)
- Предусловия (preconditions) для изоляции тестового окружения
- Пошаговые UI-сценарии с указанием ожидаемых состояний элементов
- Правила валидации и обработку граничных случаев

---

##  Примечания для тестирования

- Некоторые фичи требуют установленных плагинов: `Git`, `GitHub Branch Source`, `Role-based Authorization Strategy`, `GitHub Authentication Plugin`. Учитывайте это в `setup` ваших автотестов.
- Настройки безопасности и `legacy API token` соответствуют стандартам Jenkins `2.541.3`. При написании тестов безопасности используйте временные токены и очищайте их в `teardown`.
- Все acceptance criteria предполагают чистый экземпляр Jenkins с аутентифицированным доступом. Рекомендуется запускать тесты в изолированных Docker-контейнерах или ephemeral-окружениях.
