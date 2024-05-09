# Чистий код у PHP

## Зміст

1. [Вступ](#Вступ)
2. [Змінні](#Змінні)
   - [Використовуйте значущі та вимовляємі імена змінних](#Використовуйте-значущі-та-вимовляємі-імена-змінних)
   - [Використовуйте однакові назви для змінних зі схожим призначенням](#Використовуйте-однакові-назви-для-змінних-зі-схожим-призначенням)
   - [Використовуйте імена, за якими легко шукати (частина 1)](#Використовуйте-імена-за-якими-легко-шукати-частина-1)
   - [Використовуйте імена, за якими легко шукати (частина 2)](#Використовуйте-імена-за-якими-легко-шукати-частина-2)
   - [Використовуйте пояснювальні змінні](#Використовуйте-пояснювальні-змінні)
   - [Уникайте глибоких вкладень (частина 1)](#Уникайте-глибоких-вкладень-частина-1)
   - [Уникайте глибоких вкладень (частина 2)](#Уникайте-глибоких-вкладень-частина-2)
   - [Уникайте ментального співставлення](#Уникайте-ментального-співставлення)
   - [Не додавайте непотрібний контекст](#Не-додавайте-непотрібний-контекст)
   - [Замість скорочених або умовних використовуйте аргументи за замовчуванням](#Замість-скорочених-або-умовних-використовуйте-аргументи-за-замовчуванням)
3. [Порівняння](#Порівняння)
   - [Використовуйте ідентичне порівняння](#Використовуйте-ідентичне-порівняння)
   - [Оператор злиття з null](#Оператор-злиття-з-null)
4. [Функції](#Функції)
   - [Аргументи функцій (в ідеалі два або менше)](#Аргументи-функцій-в-ідеалі-два-або-менше)
   - [Імена функцій повинні бути говорючими](#Імена-функцій-повинні-бути-говорючими)
   - [Функції повинні бути на одному рівні абстракції](#Функції-повинні-бути-на-одному-рівні-абстракції)
   - [Не використовуйте прапорці як параметри функцій](#Не-використовуйте-прапорці-як-параметри-функцій)
   - [Уникайте побічних ефектів](#Уникайте-побічних-ефектів)
   - [Не пишіть у глобальні функції](#Не-пишіть-у-глобальні-функції)
   - [Не використовуйте шаблон Одинак (Singleton)](#Не-використовуйте-шаблон-Одинак-singleton)
   - [Інкапсулювання умовних виразів](#Інкапсулювання-умовних-виразів)
   - [Уникайте негативних умовних виразів](#Уникайте-негативних-умовних-виразів)
   - [Уникайте умовних виразів](#Уникайте-умовних-виразів)
   - [Уникайте перевірки типів (частина 1)](#Уникайте-перевірки-типів-частина-1)
   - [Уникайте перевірки типів (частина 2)](#Уникайте-перевірки-типів-частина-2)
   - [Видаляйте мертвий код](#Видаляйте-мертвий-код)
5. [Об'єкти та структури даних](#Об'єкти-та-структури-даних)
   - [Використовуйте інкапсуляцію об'єктів](#Використовуйте-інкапсуляцію-об'єктів)
   - [У об'єктів мають бути `private`/`protected` компоненти](#У-об'єктів-мають-бути-privateprotected-компоненти)
6. [Класи](#Класи)
   - [Композиція краще спадкування](#Композиція-краще-спадкування)
   - [Уникайте флуентного інтерфейсу (`Fluent interface`)](#Уникайте-флуентного-інтерфейсу-fluent-interface)
   - [Бажано використовувати `final` класи](#Бажано-використовувати-final-класи)
7. [SOLID](#solid)
   - [Принцип відкритості/закритості (Open/Closed Principle, OCP)](#Принцип-відкритостізакритості-openclosed-principle-ocp)
   - [Принцип підстановки Барбари Лісков (Liskov Substitution Principle, LSP)](#Принцип-підстановки-Барбари-Лісков-liskov-substitution-principle-lsp)
   - [Принцип розділення інтерфейсу (Interface Segregation Principle, ISP)](#Принцип-розділення-інтерфейсу-interface-segregation-principle-isp)
   - [Принцип інверсії залежностей (Dependency Inversion Principle, DIP)](#Принцип-інверсії-залежностей-dependency-inversion-principle-dip)
8. [Не повторюйся (Don’t repeat yourself, DRY)](#Не-повторюйся-dont-repeat-yourself-dry)
9. [Переклади](#Переклади)

## Вступ

Це принципи розробки програмного забезпечення, взяті з книги [_Чистий код_](https://fabulabook.com/info-chystyj-kod-7391) Роберта Мартина та адаптовані для PHP. Цей посібник не стосується стилів програмування, а допомагає створювати читабельний, багаторазово використовуваний та легкий для рефакторингу код на PHP.

Ці принципи не обов'язкові для суворого дотримання, і не всі з ними погодяться. Це лише рекомендації, засновані на багаторічному досвіді автора _Clean Code_.

Натхнений [clean-code-javascript](https://github.com/ryanmcdermott/clean-code-javascript).

Хоча багато розробників все ще використовують PHP 5, більшість прикладів у цій статті працюють лише з PHP 7.1+.

## Змінні

### Використовуйте значущі та вимовні імена змінних

**Погано:**

```php
$ymdstr = $moment->format('y-m-d');
```

**Гарно:**

```php
$currentDate = $moment->format('y-m-d');
```

**[⬆ повернутися до змісту](#Зміст)**

### Використовуйте одну й ту саму назву для змінних із однаковим призначенням

**Погано:**

```php
getUserInfo();
getUserData();
getUserRecord();
getUserProfile();
```

**Гарно:**

```php
getUser();
```

**[⬆ повернутися до змісту](#Зміст)**

### Використовуйте імена, які зручно шукати (частина 1)

Ми будемо більше читати код, ніж писати. Тому важливо писати такий код, який буде читабельним та зручним для пошуку. Але даючи змінним імена, марні для розуміння нашої програми, ми заважаємо майбутнім читачам. Використовуйте такі імена, які зручно шукати.

**Погано:**

```php
// What the heck is 448 for?
$result = $serializer->serialize($data, 448);
```

**Гарно:**

```php
$json = $serializer->serialize($data, JSON_UNESCAPED_SLASHES | JSON_PRETTY_PRINT | JSON_UNESCAPED_UNICODE);
```

### Використовуйте імена, які зручно шукати (частина 2)

**Погано:**

```php
class User
{
    // What the heck is 7 for?
    public $access = 7;
}

// What the heck is 4 for?
if ($user->access & 4) {
    // ...
}

// What's going on here?
$user->access ^= 2;
```

**Гарно:**

```php
class User
{
    public const ACCESS_READ = 1;
    public const ACCESS_CREATE = 2;
    public const ACCESS_UPDATE = 4;
    public const ACCESS_DELETE = 8;

    // User as default can read, create and update something
    public $access = self::ACCESS_READ | self::ACCESS_CREATE | self::ACCESS_UPDATE;
}

if ($user->access & User::ACCESS_UPDATE) {
    // do edit ...
}

// Deny access rights to create something
$user->access ^= User::ACCESS_CREATE;
```

**[⬆ повернутися до змісту](#Зміст)**

### Використовуйте пояснювальні змінні

**Погано:**

```php
$address = 'One Infinite Loop, Cupertino 95014';
$cityZipCodeRegex = '/^[^,]+,\s*(.+?)\s*(\d{5})$/';
preg_match($cityZipCodeRegex, $address, $matches);

saveCityZipCode($matches[1], $matches[2]);
```

**Краще:**

Так краще, але ми все одно ще сильно залежимо від регулярного виразу.

```php
$address = 'One Infinite Loop, Cupertino 95014';
$cityZipCodeRegex = '/^[^,]+,\s*(.+?)\s*(\d{5})$/';
preg_match($cityZipCodeRegex, $address, $matches);

[, $city, $zipCode] = $matches;
saveCityZipCode($city, $zipCode);
```

**Гарно:**

За допомогою назви підпаттернів знижуємо залежність від регулярного виразу.

```php
$address = 'One Infinite Loop, Cupertino 95014';
$cityZipCodeRegex = '/^[^,]+,\s*(?<city>.+?)\s*(?<zipCode>\d{5})$/';
preg_match($cityZipCodeRegex, $address, $matches);

saveCityZipCode($matches['city'], $matches['zipCode']);
```

**[⬆ повернутися до змісту](#Зміст)**

### Уникайте глибоких вкладень (частина 1)

Занадто багато `if/else` стверджень може зробити ваш код важко супроводжуваним. Явне краще за неявне.

**Погано:**

```php
function isShopOpen($day): bool
{
    if ($day) {
        if (is_string($day)) {
            $day = strtolower($day);
            if ($day === 'friday') {
                return true;
            } elseif ($day === 'saturday') {
                return true;
            } elseif ($day === 'sunday') {
                return true;
            } else {
                return false;
            }
        } else {
            return false;
        }
    } else {
        return false;
    }
}
```

**Гарно:**

```php
function isShopOpen(string $day): bool
{
    if (empty($day)) {
        return false;
    }

    $openingDays = [
        'friday', 'saturday', 'sunday'
    ];

    return in_array(strtolower($day), $openingDays, true);
}
```

**[⬆ повернутися до змісту](#Зміст)**

### Уникайте глибоких вкладень (частина 2)

**Погано:**

```php
function fibonacci(int $n)
{
    if ($n < 50) {
        if ($n !== 0) {
            if ($n !== 1) {
                return fibonacci($n - 1) + fibonacci($n - 2);
            } else {
                return 1;
            }
        } else {
            return 0;
        }
    } else {
        return 'Not supported';
    }
}
```

**Гарно:**

```php
function fibonacci(int $n): int
{
    if ($n === 0 || $n === 1) {
        return $n;
    }

    if ($n >= 50) {
        throw new \Exception('Not supported');
    }

    return fibonacci($n - 1) + fibonacci($n - 2);
}
```

**[⬆ повернутися до змісту](#Зміст)**

### Уникайте ментального зіставлення

Не змушуйте тих, хто читатиме ваш код, переводити значення змінних. Краще писати явно, аніж неявно.

**Погано:**

```php
$l = ['Austin', 'New York', 'San Francisco'];

for ($i = 0; $i < count($l); $i++) {
    $li = $l[$i];
    doStuff();
    doSomeOtherStuff();
    // ...
    // ...
    // ...
    // Wait, what is `$li` for again?
    dispatch($li);
}
```

**Гарно:**

```php
$locations = ['Austin', 'New York', 'San Francisco'];

foreach ($locations as $location) {
    doStuff();
    doSomeOtherStuff();
    // ...
    // ...
    // ...
    dispatch($location);
}
```

**[⬆ повернутися до змісту](#Зміст)**

### Не додавайте зайвий контекст

Якщо ім'я вашого класу/об'єкта з чимось асоціюється особисто для вас, не проектуйте цю асоціацію на ім'я змінної.

**Погано:**

```php
class Car
{
    public $carMake;
    public $carModel;
    public $carColor;

    //...
}
```

**Гарно:**

```php
class Car
{
    public $make;
    public $model;
    public $color;

    //...
}
```

**[⬆ повернутися до змісту](#Зміст)**

### Замість скорочених або умовних використовуйте аргументи за замовчуванням

**Не добре:**

Але не добре тому, що змінна `$breweryName` може бути `NULL`.

```php
function createMicrobrewery($breweryName = 'Hipster Brew Co.'): void
{
    // ...
}
```

**Краще:**

Це рішення менш зрозуміле, ніж попередня версія, але краще контролює значення змінної.

```php
function createMicrobrewery($name = null): void
{
    $breweryName = $name ?: 'Hipster Brew Co.';
    // ...
}
```

**Гарно:**

Ви можете використовувати [контроль типів](https://www.php.net/manual/en/language.types.declarations.php) і бути впевненим, що змінна `$breweryName` ніколи не буде `NULL`.

```php
function createMicrobrewery(string $breweryName = 'Hipster Brew Co.'): void
{
    // ...
}
```

**[⬆ повернутися до змісту](#Зміст)**

## Порівняння

### Використовуйте [тотожнє порівняння](https://www.php.net/manual/en/language.operators.comparison.php)

**Не добре:**

При використанні простого порівняння, string буде перетворено на integer.

```php
$a = '42';
$b = 42;

if ($a != $b) {
   // The expression will always pass
}
```

Порівняння `$a! = $b` повертає `FALSE`, але насправді це `TRUE`!
Рядок `42` відрізняється від рядка числа `42`.

**Гарно:**

Використовуючи тотожнє порівняння, порівнюватимуться тип і значення.

```php
$a = '42';
$b = 42;

if ($a !== $b) {
    // The expression is verified
}
```

Порівняння `$a !== $b` повертає `TRUE`.

**[⬆ повернутися до змісту](#Зміст)**

### Оператор поєднання з null

Нульове об'єднання - це новий оператор, [введений у PHP 7] (https://www.php.net/manual/en/migration70.new-features.php#migration70.new-features.null-coalesce-op).
Оператор поєднання з null (`??`), що є синтаксичним цукром для досить поширеної дії, коли
спільно використовуються тернарний оператор та функція `isset()`. Він повертає перший операнд, якщо він заданий і не дорівнює
`NULL`, а у протилежному випадку повертає другий операнд.

**Не добре:**

```php
if (isset($_GET['name'])) {
    $name = $_GET['name'];
} elseif (isset($_POST['name'])) {
    $name = $_POST['name'];
} else {
    $name = 'nobody';
}
```

**Гарно:**

```php
$name = $_GET['name'] ?? $_POST['name'] ?? 'nobody';
```

**[⬆ повернутися до змісту](#Зміст)**

## Функції

### Аргументи функцій (краще два або менше)

Дуже важливо обмежувати кількість параметрів функцій, оскільки це полегшує тестування. Більше трьох аргументів призводить до "комбінаторного вибуху", коли вам потрібно протестувати багато різних випадків для кожного аргументу.

Ідеальний варіант — взагалі без аргументів. Один-два також нормально, але трьох потрібно уникати. Якщо їх більше, потрібно їх об'єднувати, щоб зменшити кількість. Зазвичай, якщо у вас більше двох аргументів, то функція виконує занадто багато завдань. У тих випадках, коли це не так, частіше за все в якості аргументу достатньо використовувати об'єкт більш високого рівня.

**Погано:**

```php
class Questionnaire
{
    public function __construct(
        string $firstname,
        string $lastname,
        string $patronymic,
        string $region,
        string $district,
        string $city,
        string $phone,
        string $email
    ) {
        // ...
    }
}
```

**Гарно:**

```php
class Name
{
    private $firstname;
    private $lastname;
    private $patronymic;

    public function __construct(string $firstname, string $lastname, string $patronymic)
    {
        $this->firstname = $firstname;
        $this->lastname = $lastname;
        $this->patronymic = $patronymic;
    }

    // getters ...
}

class City
{
    private $region;
    private $district;
    private $city;

    public function __construct(string $region, string $district, string $city)
    {
        $this->region = $region;
        $this->district = $district;
        $this->city = $city;
    }

    // getters ...
}

class Contact
{
    private $phone;
    private $email;

    public function __construct(string $phone, string $email)
    {
        $this->phone = $phone;
        $this->email = $email;
    }

    // getters ...
}

class Questionnaire
{
    public function __construct(Name $name, City $city, Contact $contact)
    {
        // ...
    }
}
```

**[⬆ повернутися до змісту](#Зміст)**

### Імена функцій повинні бути такими, що говорять

**Погано:**

```php
class Email
{
    //...

    public function handle(): void
    {
        mail($this->to, $this->subject, $this->body);
    }
}

$message = new Email(...);
// What is this? A handle for the message? Are we writing to a file now?
$message->handle();
```

**Гарно:**

```php
class Email
{
    //...

    public function send(): void
    {
        mail($this->to, $this->subject, $this->body);
    }
}

$message = new Email(...);
// Clear and obvious
$message->send();
```

**[⬆ повернутися до змісту](#Зміст)**

### Функції мають бути лише єдиним рівнем абстракції

Якщо у вас кілька рівнів абстракції, то на функцію покладено багато завдань. Розбиття функцій дозволяє багаторазово використовувати код та полегшує тестування.

**Погано:**

```php
function parseBetterPHPAlternative(string $code): void
{
    $regexes = [
        // ...
    ];

    $statements = explode(' ', $code);
    $tokens = [];
    foreach ($regexes as $regex) {
        foreach ($statements as $statement) {
            // ...
        }
    }

    $ast = [];
    foreach ($tokens as $token) {
        // lex...
    }

    foreach ($ast as $node) {
        // parse...
    }
}
```

**Теж погано:**

Ми виконали деякі функції, але функція `parseBetterPHPAlternative()` все ще дуже складна і не тестується.

```php
function tokenize(string $code): array
{
    $regexes = [
        // ...
    ];

    $statements = explode(' ', $code);
    $tokens = [];
    foreach ($regexes as $regex) {
        foreach ($statements as $statement) {
            $tokens[] = /* ... */;
        }
    }

    return $tokens;
}

function lexer(array $tokens): array
    $ast = [];
{
    foreach ($tokens as $token) {
        $ast[] = /* ... */;
    }

    return $ast;
}

function parseBetterPHPAlternative(string $code): void
{
    $tokens = tokenize($code);
    $ast = lexer($tokens);
    foreach ($ast as $node) {
        // parse...
    }
}
```

**Гарно:**

Найкращим рішенням є винесення всіх залежностей з функції `parseBetterPHPAlternative()`.

```php
class Tokenizer
{
    public function tokenize(string $code): array
    {
        $regexes = [
            // ...
        ];

        $statements = explode(' ', $code);
        $tokens = [];
        foreach ($regexes as $regex) {
            foreach ($statements as $statement) {
                $tokens[] = /* ... */;
            }
        }

        return $tokens;
    }
}

class Lexer
{
    public function lexify(array $tokens): array
    {
        $ast = [];
        foreach ($tokens as $token) {
            $ast[] = /* ... */;
        }

        return $ast;
    }
}

class BetterPHPAlternative
{
    private $tokenizer;
    private $lexer;

    public function __construct(Tokenizer $tokenizer, Lexer $lexer)
    {
        $this->tokenizer = $tokenizer;
        $this->lexer = $lexer;
    }

    public function parse(string $code): void
    {
        $tokens = $this->tokenizer->tokenize($code);
        $ast = $this->lexer->lexify($tokens);
        foreach ($ast as $node) {
            // parse...
        }
    }
}
```

**[⬆ повернутися до змісту](#Зміст)**

### Не використовуйте прапори як параметри функцій

Прапори кажуть вашим користувачам, що функції роблять більше однієї речі. А вони мають робити щось одне. Розділяйте свої функції, якщо вони йдуть різними гілками коду відповідно до булевої логіки.

**Погано:**

```php
function createFile(string $name, bool $temp = false): void
{
    if ($temp) {
        touch('./temp/'.$name);
    } else {
        touch($name);
    }
}
```

**Гарно:**

```php
function createFile(string $name): void
{
    touch($name);
}

function createTempFile(string $name): void
{
    touch('./temp/'.$name);
}
```

**[⬆ повернутися до змісту](#Зміст)**

### Уникайте побічних ефектів

Функція може привносити побічні ефекти, якщо вона отримує значення і не лише повертає інше значення/значення, а й робить щось ще. Побічним ефектом може бути запис у файл, зміна глобальної змінної або випадкове відправлення всіх грошей незнайомій людині.

Але іноді побічні ефекти бувають потрібні. Наприклад, той самий запис у файл. Найкраще робити це централізовано. Не вибирайте кілька функцій і класів, які пишуть в один файл, використовуйте для цього єдиний сервіс. Єдиний.

Головне завдання - уникнути поширених помилок на кшталт загального стану для кількох об'єктів без будь-якої структури; використання змінюваних типів даних, які можуть бути чимось перезаписані; відсутність централізованої обробки побічних ефектів. Якщо ви зможете це зробити, то будете щасливішими за переважну більшість інших програмістів.

**Погано:**

```php
// Global variable referenced by following function.
// If we had another function that used this name, now it'd be an array and it could break it.
$name = 'Ryan McDermott';

function splitIntoFirstAndLastName(): void
{
    global $name;

    $name = explode(' ', $name);
}

splitIntoFirstAndLastName();

var_dump($name); // ['Ryan', 'McDermott'];
```

**Гарно:**

```php
function splitIntoFirstAndLastName(string $name): array
{
    return explode(' ', $name);
}

$name = 'Ryan McDermott';
$newName = splitIntoFirstAndLastName($name);

var_dump($name); // 'Ryan McDermott';
var_dump($newName); // ['Ryan', 'McDermott'];
```

**[⬆ повернутися до змісту](#Зміст)**

### Не пишіть у глобальні функції

Засмічення глобалами - погана звичка в будь-якій мові, тому що ви можете конфліктувати з іншою бібліотекою, а користувачі вашого API не знатимуть про це, поки не отримають виняток у production. Наведу приклад: вам потрібний конфігураційний масив? Ви пишете глобальну функцію на зразок `config()`, але вона може конфліктувати з іншою бібліотекою, яка намагається робити те саме.

**Погано:**

```php
function config(): array
{
    return  [
        'foo' => 'bar',
    ];
}
```

**Гарно:**

```php
class Configuration
{
    private $configuration = [];

    public function __construct(array $configuration)
    {
        $this->configuration = $configuration;
    }

    public function get(string $key): ?string
    {
        // null coalescing operator
        return $this->configuration[$key] ?? null;
    }
}
```

Завантажте конфігурацію та створіть екземпляр класу `Configuration`.

```php
$configuration = new Configuration([
    'foo' => 'bar',
]);
```

І тепер ви повинні використовувати екземпляр класу `Configuration` у своєму додатку.

**[⬆ повернутися до змісту](#Зміст)**

### Не використовуйте шаблон Одинак (Singleton)

Шаблон проектування Одинак (Singleton) є [антипатерном] (<https://uk.wikipedia.org/wiki/Одинак_(шаблон_проєктування)>). Перефразуємо Brian Button:

1. Як правило, одинаки використовуються як **глобальний екземпляр**, чому це так погано? Тому що ви **приховуєте залежності вашої програми** у своєму коді, замість того, щоб зробити їх явними через інтерфейси. Зробити щось глобальним, щоб уникнути його поширення - це [чимось тхне](https://uk.wikipedia.org/wiki/Запахи_коду).
2. Одинаки порушують принцип [єдиної відповідальності](#Принцип-єдиної-відповідальності-single-responsibility-principle-srp): через те, що **вони контролюють власне створення і життєвий цикл**.
3. Одинаки за своєю суттю призводять до того, що код виходить тісно [пов'язаним] (<https://uk.wikipedia.org/wiki/Зв%27язність_(програмування)>). Це в багатьох випадках ускладнює його тестування.
4. Одинаки несуть стан протягом усього життя програми. Ще один удар по тестуванню, **так як ви можете зіткнутися із ситуацією, коли необхідно закінчити тести**, що є великим немає для модульних тестів. Навіщо? Тому що кожен модульний тест має бути незалежним від іншого.

**Погано:**

```php
class DBConnection
{
    private static $instance;

    private function __construct(string $dsn)
    {
        // ...
    }

    public static function getInstance(): DBConnection
    {
        if (self::$instance === null) {
            self::$instance = new self();
        }

        return self::$instance;
    }

    // ...
}

$singleton = DBConnection::getInstance();
```

**Гарно:**

```php
class DBConnection
{
    public function __construct(string $dsn)
    {
        // ...
    }

     // ...
}
```

Створіть екземпляр класу `DBConnection` та налаштуйте його за допомогою [DSN](https://www.php.net/manual/en/pdo.construct.php#refsect1-pdo.construct-parameters).

```php
$connection = new DBConnection($dsn);
```

І тепер ви повинні використовувати екземпляр класу `DBConnection` у своїй програмі.

**[⬆ повернутися до змісту](#Зміст)**

### Інкапсулювання умовних виразів

**Погано:**

```php
if ($article->state === 'published') {
    // ...
}
```

**Гарно:**

```php
if ($article->isPublished()) {
    // ...
}
```

**[⬆ повернутися до змісту](#Зміст)**

### Уникайте негативних умовних виразів

**Погано:**

```php
function isDOMNodeNotPresent(\DOMNode $node): bool
{
    // ...
}

if (!isDOMNodeNotPresent($node))
{
    // ...
}
```

**Гарно:**

```php
function isDOMNodePresent(\DOMNode $node): bool
{
    // ...
}

if (isDOMNodePresent($node)) {
    // ...
}
```

**[⬆ повернутися до змісту](#Зміст)**

### Уникайте умовних виразів

Напевно, це здається неможливим. Вперше це почувши, багато хто каже: "Як я зможу щось зробити без виразу `if`?" Друге поширене питання: "Ну, це чудово, але навіщо мені це?" Відповідь полягає у розглянутому вище правилі чистого коду: функція має робити щось одне. Якщо у вас є класи та функції, що містять вираз `if`, то тим самим ви кажете своїм користувачам, що функція робить більше однієї речі. Не забувайте – треба залишити щось одне.

**Погано:**

```php
class Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        switch ($this->type) {
            case '777':
                return $this->getMaxAltitude() - $this->getPassengerCount();
            case 'Air Force One':
                return $this->getMaxAltitude();
            case 'Cessna':
                return $this->getMaxAltitude() - $this->getFuelExpenditure();
        }
    }
}
```

**Гарно:**

```php
interface Airplane
{
    // ...

    public function getCruisingAltitude(): int;
}

class Boeing777 implements Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        return $this->getMaxAltitude() - $this->getPassengerCount();
    }
}

class AirForceOne implements Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        return $this->getMaxAltitude();
    }
}

class Cessna implements Airplane
{
    // ...

    public function getCruisingAltitude(): int
    {
        return $this->getMaxAltitude() - $this->getFuelExpenditure();
    }
}
```

**[⬆ повернутися до змісту](#Зміст)**

### Уникайте перевірки типів (частина 1)

PHP не типизований, тобто ваші функції можуть приймати аргументи будь-яких типів. Іноді така свобода навіть заважає і виникає спокуса виконувати перевірку типів у функціях. Але є багато способів цього уникнути. Перше, що потрібно враховувати, це узгоджені API.

**Погано:**

```php
function travelToTexas($vehicle): void
{
    if ($vehicle instanceof Bicycle) {
        $vehicle->pedalTo(new Location('texas'));
    } elseif ($vehicle instanceof Car) {
        $vehicle->driveTo(new Location('texas'));
    }
}
```

**Гарно:**

```php
function travelToTexas(Vehicle $vehicle): void
{
    $vehicle->travelTo(new Location('texas'));
}
```

**[⬆ повернутися до змісту](#Зміст)**

### Уникайте перевірки типів (частина 2)

Якщо ви працюєте з базовими примітивами (на кшталт рядкових, цілісних) і масивами, то не можете використовувати поліморфізм. Але якщо здається, що вам потрібна перевірка типів і ви використовуєте PHP 7+, то застосуйте [оголошення типів](https://www.php.net/manual/en/language.types.declarations.php) або строгий режим (Strict mode). Це дасть вам статичну типізацію поверх стандартного PHP-синтаксису. Проблема ручної перевірки типів у тому, що її якісне виконання має на увазі таку багатослівність, що отримана штучна "типобезпека" не компенсує втрати читабельності коду. Зберігайте чистоту свого коду, пишіть хороші тести та проводьте якісні ревізії коду. Або робіть все це, але із суворим оголошенням PHP-типів або в строгому режимі.

**Погано:**

```php
function combine($val1, $val2): int
{
    if (!is_numeric($val1) || !is_numeric($val2)) {
        throw new \Exception('Must be of type Number');
    }

    return $val1 + $val2;
}
```

**Гарно:**

```php
function combine(int $val1, int $val2): int
{
    return $val1 + $val2;
}
```

**[⬆ повернутися до змісту](#Зміст)**

### Забирайте мертвий код

Він поганий так само, як і код, що дублюється. Не потрібно тримати його в кодовій базі. Якщо щось не викликається, позбавтеся цього! Якщо знадобиться, мертвий код можна дістати з історії версій.

**Погано:**

```php
function oldRequestModule(string $url): void
{
    // ...
}

function newRequestModule(string $url): void
{
    // ...
}

$request = newRequestModule($requestUrl);
inventoryTracker('apples', $request, 'www.inventory-awesome.io');
```

**Гарно:**

```php
function requestModule(string $url): void
{
    // ...
}

$request = requestModule($requestUrl);
inventoryTracker('apples', $request, 'www.inventory-awesome.io');
```

**[⬆ повернутися до змісту](#Зміст)**

## Об'єкти та структури даних

### Використовуйте інкапсуляцію об'єктів

У PHP можна задати для методів ключові слова `public`, `protected` та `private`. З їх допомогою ви керуватимете зміною властивостей об'єкта.

- Якщо вам потрібно не тільки отримувати властивість об'єкта, то необов'язково знаходити та змінювати кожен метод читання (accessor) у кодовій базі.
- Завдяки `set` простіше додати валідацію.
- Можна інкапсулювати внутрішнє уявлення.
- За допомогою геттерів та сеттерів легко додавати журналування та обробку помилок.
- При успадкуванні такого класу можна перевизначити функціональність за замовчуванням.
- Ви можете ліниво завантажувати властивості об'єкта, наприклад, отримуючи їх із сервера.

Також це частина принципу [Відкритості/Закритості](#Принцип-відкритостізакритості-openclosed-principle-ocp), що входить у набір об'єктно-орієнтованих принципів проектування.

**Погано:**

```php
class BankAccount
{
    public $balance = 1000;
}

$bankAccount = new BankAccount();

// Buy shoes...
$bankAccount->balance -= 100;
```

**Гарно:**

```php
class BankAccount
{
    private $balance;

    public function __construct(int $balance = 1000)
    {
      $this->balance = $balance;
    }

    public function withdraw(int $amount): void
    {
        if ($amount > $this->balance) {
            throw new \Exception('Amount greater than available balance.');
        }

        $this->balance -= $amount;
    }

    public function deposit(int $amount): void
    {
        $this->balance += $amount;
    }

    public function getBalance(): int
    {
        return $this->balance;
    }
}

$bankAccount = new BankAccount();

// Buy shoes...
$bankAccount->withdraw($shoesPrice);

// Get balance
$balance = $bankAccount->getBalance();
```

**[⬆ повернутися до змісту](#Зміст)**

### Об'єкти повинні мати private/protected компоненти

- `public` методи та властивості найбільш небезпечні для змін, оскільки зовнішній код може легко спиратися на них, і ви не можете контролювати, який код спирається на них. **Зміни в класі небезпечні для всіх користувачів класу.**
- `protected` модифікатор є так само небезпечними, як і `public`, оскільки вони доступні в рамках будь-якого дочірнього класу. Це фактично означає, що різниця між `public` та `protected` є лише механізмом доступу, але гарантія інкапсуляції залишається незмінною. **Модифікації у класі небезпечні всім класів нащадків.**
- `private` модифікатор гарантує, що код **небезпечний для зміни тільки в межах одного класу** (ви захищені від модифікацій, і у вас не буде [Jenga ефекту](http://www.urbandictionary.com/define.php?term=Jengaphobia&defid=2494196)).

Тому використовуйте `private` за замовчуванням та `public/protected`, коли вам потрібно надати доступ для зовнішніх класів.

Для отримання додаткової інформації ви можете прочитати [повідомлення у блозі](http://fabien.potencier.org/pragmatism-over-theory-protected-vs-private.html), написане [Fabien Potencier](https://github.com/fabpot).

**Погано:**

```php
class Employee
{
    public $name;

    public function __construct(string $name)
    {
        $this->name = $name;
    }
}

$employee = new Employee('John Doe');
echo 'Employee name: '.$employee->name; // Employee name: John Doe
```

**Гарно:**

```php
class Employee
{
    private $name;

    public function __construct(string $name)
    {
        $this->name = $name;
    }

    public function getName(): string
    {
        return $this->name;
    }
}

$employee = new Employee('John Doe');
echo 'Employee name: '.$employee->getName(); // Employee name: John Doe
```

**[⬆ повернутися до змісту](#Зміст)**

## Класи

### Композиція краща за успадкування

Як йдеться у відомій книзі "[_ Шаблони проектування_](<https://uk.wikipedia.org/wiki/Design_Patterns_(книга)>)" Банди чотирьох, у міру можливості потрібно вибирати композицію, а не успадкування. Є багато добрих причин використовувати як успадкування, так і композицію. Головна мета цієї максими полягає в тому, якщо ви інстинктивно схиляєтеся до успадкування, то постарайтеся уявити, чи може композиція краще вирішити ваше завдання. У якихось випадках це справді більш слушний варіант.

Ви запитаєте: "А коли краще вибирати спадкування?" Все залежить від конкретного завдання, але можна орієнтуватися на цей перелік ситуацій, коли спадкування краще композиції:

1. Ваше успадкування - це взаємозв'язок is-a, а не has-a. Приклад: Людина → Тварина vs. Користувач → Деталі користувача (UserDetails).
2. Ви можете повторно використовувати код із базових класів. (Люди можуть рухатися, як тварини.)
3. Ви хочете внести глобальні зміни до похідних класів, змінивши базовий клас. (Зміна витрати калорій у тварин під час руху.)

**Погано:**

```php
class Employee
{
    private $name;
    private $email;

    public function __construct(string $name, string $email)
    {
        $this->name = $name;
        $this->email = $email;
    }

    // ...
}

// Bad because Employees "have" tax data.
// EmployeeTaxData is not a type of Employee

class EmployeeTaxData extends Employee
{
    private $ssn;
    private $salary;

    public function __construct(string $name, string $email, string $ssn, string $salary)
    {
        parent::__construct($name, $email);

        $this->ssn = $ssn;
        $this->salary = $salary;
    }

    // ...
}
```

**Гарно:**

```php
class EmployeeTaxData
{
    private $ssn;
    private $salary;

    public function __construct(string $ssn, string $salary)
    {
        $this->ssn = $ssn;
        $this->salary = $salary;
    }

    // ...
}

class Employee
{
    private $name;
    private $email;
    private $taxData;

    public function __construct(string $name, string $email)
    {
        $this->name = $name;
        $this->email = $email;
    }

    public function setTaxData(EmployeeTaxData $taxData)
    {
        $this->taxData = $taxData;
    }

    // ...
}
```

**[⬆ повернутися до змісту](#Зміст)**

### Уникати Поточний інтерфейс (Fluent interface)

[Поточний інтерфейс (Fluent interface)](https://uk.wikipedia.org/wiki/Fluent_interface) - це об'єктно-орієнтований API, метою якого є покращення читабельності вихідного коду за допомогою [Ланцюжків методів (Method chaining)](https://en.wikipedia.org/wiki/Method_chaining).

Хоча можуть бути деякі випадки, коли цей шаблон зменшує багатослівність коду (наприклад, [PHPUnit Mock Builder](https://phpunit.de/manual/current/en/test-doubles.html) або [Doctrine Query Builder](http://docs.doctrine-project.org/projects/doctrine-dbal/en/latest/reference/query-builder.html)), але найчастіше це відбувається з деякими витратами:

1. Порушення [Інкапсуляції] (<https://uk.wikipedia.org/wiki/Інкапсуляція_(програмування)>).
2. Порушення [Декораторів] (<https://uk.wikipedia.org/wiki/Декоратор_(шаблон_проектування)>).
3. Ускладнює [мокінг (mock)] (https://uk.wikipedia.org/wiki/Макет_об%27єкта) у тестах.
4. Ускладнює читання diff комітів.

Для отримання додаткової інформації ви можете прочитати [повідомлення у блозі](https://ocramius.github.io/blog/fluent-interfaces-are-evil/), написане [Marco Pivetta](https://github.com/Ocramius).

**Погано:**

```php
class Car
{
    private $make = 'Honda';
    private $model = 'Accord';
    private $color = 'white';

    public function setMake(string $make): self
    {
        $this->make = $make;

        // NOTE: Returning this for chaining
        return $this;
    }

    public function setModel(string $model): self
    {
        $this->model = $model;

        // NOTE: Returning this for chaining
        return $this;
    }

    public function setColor(string $color): self
    {
        $this->color = $color;

        // NOTE: Returning this for chaining
        return $this;
    }

    public function dump(): void
    {
        var_dump($this->make, $this->model, $this->color);
    }
}

$car = (new Car())
  ->setColor('pink')
  ->setMake('Ford')
  ->setModel('F-150')
  ->dump();
```

**Гарно:**

```php
class Car
{
    private $make = 'Honda';
    private $model = 'Accord';
    private $color = 'white';

    public function setMake(string $make): void
    {
        $this->make = $make;
    }

    public function setModel(string $model): void
    {
        $this->model = $model;
    }

    public function setColor(string $color): void
    {
        $this->color = $color;
    }

    public function dump(): void
    {
        var_dump($this->make, $this->model, $this->color);
    }
}

$car = new Car();
$car->setColor('pink');
$car->setMake('Ford');
$car->setModel('F-150');
$car->dump();
```

**[⬆ повернутися до змісту](#Зміст)**

### Краще final класи

`final` повинен використовуватися щоразу, коли це можливо:

1. Це запобігає неконтрольованому ланцюжку успадкування.
2. Заохочує [композицію](#Композиція-краще-успадкування).
3. Заохочує [Single Responsibility Principle](#Принцип-єдиної-відповідальності-single-responsibility-principle-srp).
4. Заохочує використовувати відкриті методи замість розширення класу для отримання доступу до захищених.
5. Це дозволяє змінювати ваш код без можливості зламати програми, які використовують ваш клас.

Єдина умова – ваш клас має реалізовувати інтерфейс і не визначати жодних інших відкритих методів.

Для отримання додаткової інформації ви можете прочитати [пост у блозі](https://ocramius.github.io/blog/when-to-declare-classes-final/) на цю тему, написану [Marco Pivetta (Ocramius)](https://ocramius.github.io/).

**Погано:**

```php
final class Car
{
    private $color;

    public function __construct($color)
    {
        $this->color = $color;
    }

    /**
     * @return string The color of the vehicle
     */
    public function getColor()
    {
        return $this->color;
    }
}
```

**Гарно:**

```php
interface Vehicle
{
    /**
     * @return string The color of the vehicle
     */
    public function getColor();
}

final class Car implements Vehicle
{
    private $color;

    public function __construct($color)
    {
        $this->color = $color;
    }

    /**
     * {@inheritdoc}
     */
    public function getColor()
    {
        return $this->color;
    }
}
```

**[⬆ повернутися до змісту](#Зміст)**

## SOLID

**SOLID** - це мнемонічний акронім, введений Michael Feathers для перших п'яти принципів об'єктно-орієнтованого програмування та дизайну, описаних Robert Martin.

- [S: Принцип єдиної відповідальності (Single Responsibility Principle, SRP)](#Принцип-єдиної-відповідальності-single-responsibility-principle-srp)
- [O: Принцип відкритості/закритості (Open/Closed Principle, OCP)](#Принцип-відкритості-закритості-openclosed-principle-ocp)
- [L: Принцип підстановки Барбари Лисків (Liskov Substitution Principle, LSP)](#Принцип-підстановки-Барбари-Лісків-liskov-substitution-principle-lsp)
- [I: Принцип поділу інтерфейсу (Interface Segregation Principle, ISP)](#Принцип-поділу-інтерфейсу-interface-segregation-principle-isp)
- [D: Принцип інверсії залежностей (Dependency Inversion Principle, DIP)](#Принцип-інверсії-залежностей-dependency-inversion-principle-dip)

### Принцип єдиної відповідальності (Single Responsibility Principle, SRP)

Як сказано в книзі Clean Code: "Для зміни класу ніколи не повинно бути більше однієї причини". Іноді привабливо набити клас всілякою функціональністю, як ми це робимо з сумками та рюкзаками, які дозволяється взяти в якості ручної поклажі в літак. Проблема в тому, що ваш клас не буде концептуально пов'язаним (conceptually cohesive), і тому виникне багато причин його змінити. Важливо мінімізувати кількість випадків, коли потрібно змінювати клас. А важливо тому, що коли в класі надлишок функціональності і вам потрібно змінити її частину, то може бути важко зрозуміти, як це позначиться на залежних модулях кодової бази.

**Погано:**

```php
class UserSettings
{
    private $user;

    public function __construct(User $user)
    {
        $this->user = $user;
    }

    public function changeSettings(array $settings): void
    {
        if ($this->verifyCredentials()) {
            // ...
        }
    }

    private function verifyCredentials(): bool
    {
        // ...
    }
}
```

**Гарно:**

```php
class UserAuth
{
    private $user;

    public function __construct(User $user)
    {
        $this->user = $user;
    }

    public function verifyCredentials(): bool
    {
        // ...
    }
}

class UserSettings
{
    private $user;
    private $auth;

    public function __construct(User $user)
    {
        $this->user = $user;
        $this->auth = new UserAuth($user);
    }

    public function changeSettings(array $settings): void
    {
        if ($this->auth->verifyCredentials()) {
            // ...
        }
    }
}
```

**[⬆ повернутися до змісту](#Зміст)**

### Принцип відкритості/закритості (Open/Closed Principle, OCP)

Як сказав Bertrand Meyer: "Програмні сутності (класи, модулі, функції тощо) повинні бути відкриті для розширення, але закриті для модифікування". Що це означає? Дозвольте користувачам додавати нову функціональність без зміни коду.

**Погано:**

```php
abstract class Adapter
{
    protected $name;

    public function getName(): string
    {
        return $this->name;
    }
}

class AjaxAdapter extends Adapter
{
    public function __construct()
    {
        parent::__construct();

        $this->name = 'ajaxAdapter';
    }
}

class NodeAdapter extends Adapter
{
    public function __construct()
    {
        parent::__construct();

        $this->name = 'nodeAdapter';
    }
}

class HttpRequester
{
    private $adapter;

    public function __construct(Adapter $adapter)
    {
        $this->adapter = $adapter;
    }

    public function fetch(string $url): Promise
    {
        $adapterName = $this->adapter->getName();

        if ($adapterName === 'ajaxAdapter') {
            return $this->makeAjaxCall($url);
        } elseif ($adapterName === 'httpNodeAdapter') {
            return $this->makeHttpCall($url);
        }
    }

    private function makeAjaxCall(string $url): Promise
    {
        // request and return promise
    }

    private function makeHttpCall(string $url): Promise
    {
        // request and return promise
    }
}
```

**Гарно:**

```php
interface Adapter
{
    public function request(string $url): Promise;
}

class AjaxAdapter implements Adapter
{
    public function request(string $url): Promise
    {
        // request and return promise
    }
}

class NodeAdapter implements Adapter
{
    public function request(string $url): Promise
    {
        // request and return promise
    }
}

class HttpRequester
{
    private $adapter;

    public function __construct(Adapter $adapter)
    {
        $this->adapter = $adapter;
    }

    public function fetch(string $url): Promise
    {
        return $this->adapter->request($url);
    }
}
```

**[⬆ повернутися до змісту](#Зміст)**

### Принцип підстановки Барбари Лисков (Liskov Substitution Principle, LSP)

За цим страшним терміном ховається дуже проста ідея. Формальне визначення: "Якщо S - це підтип Т, то об'єкти типу Т можуть бути замінені об'єктами типу S (наприклад, замість об'єктів типу Т можна підставити об'єкти типу S) без зміни будь-яких властивостей програми (коректність, завдання тощо). )". Ще більш страшне визначення.

Можна пояснити простіше: якщо у вас є батьківський та дочірній класи, тоді вони можуть бути взаємозамінними без отримання некоректних результатів. Розглянемо класичний приклад із квадратом і прямокутником. З точки зору математики квадрат — це прямокутник, але якщо змоделювати цей взаємозв'язок is-a у вигляді спадкування, то у вас будуть проблеми.

**Погано:**

```php
class Rectangle
{
    protected $width = 0;
    protected $height = 0;

    public function setWidth(int $width): void
    {
        $this->width = $width;
    }

    public function setHeight(int $height): void
    {
        $this->height = $height;
    }

    public function getArea(): int
    {
        return $this->width * $this->height;
    }
}

class Square extends Rectangle
{
    public function setWidth(int $width): void
    {
        $this->width = $this->height = $width;
    }

    public function setHeight(int $height): void
    {
        $this->width = $this->height = $height;
    }
}

function printArea(Rectangle $rectangle): void
{
    $rectangle->setWidth(4);
    $rectangle->setHeight(5);

    // BAD: Will return 25 for Square. Should be 20.
    echo sprintf('%s has area %d.', get_class($rectangle), $rectangle->getArea()).PHP_EOL;
}

$rectangles = [new Rectangle(), new Square()];

foreach ($rectangles as $rectangle) {
    printArea($rectangle);
}
```

**Гарно:**

Найкращий спосіб - розділити чотирикутники та виділити більш загальний підтип для обох фігур.

Незважаючи на уявну подібність квадрата і прямокутника, вони різні.
Квадрат має багато спільного з ромбом, а прямокутник з паралелограмом, але вони не є підтипом.
Квадрат, прямокутник, ромб і паралелограм - це окремі фігури зі своїми власними властивостями, хоч і схожими.

```php
interface Shape
{
    public function getArea(): int;
}

class Rectangle implements Shape
{
    private $width = 0;
    private $height = 0;

    public function __construct(int $width, int $height)
    {
        $this->width = $width;
        $this->height = $height;
    }

    public function getArea(): int
    {
        return $this->width * $this->height;
    }
}

class Square implements Shape
{
    private $length = 0;

    public function __construct(int $length)
    {
        $this->length = $length;
    }

    public function getArea(): int
    {
        return $this->length ** 2;
    }
}

function printArea(Shape $shape): void
{
    echo sprintf('%s has area %d.', get_class($shape), $shape->getArea()).PHP_EOL;
}

$shapes = [new Rectangle(4, 5), new Square(5)];

foreach ($shapes as $shape) {
    printArea($shape);
}
```

**[⬆ повернутися до змісту](#Зміст)**

### Принцип поділу інтерфейсу (Interface Segregation Principle, ISP)

Згідно з ISP, "Клієнти не повинні залежати від інтерфейсів, які не використовують".

Хороший приклад демонстрації принципу: класи, котрим потрібні великі об'єкти налаштувань (settings objects). Рекомендується не вимагати від клієнтів налаштовувати багато параметрів, тому що вони здебільшого їм не потрібні. Якщо зробити їх опціональними, це допоможе уникнути роздутості інтерфейсу.

**Погано:**

```php
interface Employee
{
    public function work(): void;

    public function eat(): void;
}

class HumanEmployee implements Employee
{
    public function work(): void
    {
        // ....working
    }

    public function eat(): void
    {
        // ...... eating in lunch break
    }
}

class RobotEmployee implements Employee
{
    public function work(): void
    {
        //.... working much more
    }

    public function eat(): void
    {
        //.... robot can't eat, but it must implement this method
    }
}
```

**Гарно:**

Не кожний працівник є співробітником, але кожен співробітник є працівником.

```php
interface Workable
{
    public function work(): void;
}

interface Feedable
{
    public function eat(): void;
}

interface Employee extends Feedable, Workable
{
}

class HumanEmployee implements Employee
{
    public function work(): void
    {
        // ....working
    }

    public function eat(): void
    {
        //.... eating in lunch break
    }
}

// robot can only work
class RobotEmployee implements Workable
{
    public function work(): void
    {
        // ....working
    }
}
```

**[⬆ повернутися до змісту](#Зміст)**

### Принцип інверсії залежностей (Dependency Inversion Principle, DIP)

Цей принцип каже:

1. Високорівневі модулі не залежать від низькорівневих. Обидва види мають залежати від абстракцій.
2. Абстракції не повинні залежати від деталей. Деталі мають залежати від абстракцій.

Спочатку це може бути важким для розуміння, але якщо ви працювали з PHP-фреймворками (на зразок Symfony), то вже зустрічалися з реалізацією цього принципу як ін'єкції залежності (Dependency Injection, DI). Однак ці принципи не ідентичні, DI захищає високорівневі модулі від деталей своїх низькорівневих модулів та їх налаштування. Це може бути зроблено за допомогою DI. Величезна перевага в тому, що знижується зчеплення між модулями. Зчеплення - дуже поганий шаблон розробки, що ускладнює рефакторинг коду.

**Погано:**

```php
class Employee
{
    public function work(): void
    {
        // ....working
    }
}

class Robot extends Employee
{
    public function work(): void
    {
        //.... working much more
    }
}

class Manager
{
    private $employee;

    public function __construct(Employee $employee)
    {
        $this->employee = $employee;
    }

    public function manage(): void
    {
        $this->employee->work();
    }
}
```

**Гарно:**

```php
interface Employee
{
    public function work(): void;
}

class Human implements Employee
{
    public function work(): void
    {
        // ....working
    }
}

class Robot implements Employee
{
    public function work(): void
    {
        //.... working much more
    }
}

class Manager
{
    private $employee;

    public function __construct(Employee $employee)
    {
        $this->employee = $employee;
    }

    public function manage(): void
    {
        $this->employee->work();
    }
}
```

**[⬆ повернутися до змісту](#Зміст)**

## Не повторюйся (Don't repeat yourself, DRY)

Постарайтеся дотримуватися принципу [DRY](https://uk.wikipedia.org/wiki/Don%27t_repeat_yourself).

Намагайтеся повністю позбутися дублюючого коду. Він поганий тим, що якщо вам потрібно змінювати логіку, то це доведеться робити в кількох місцях.

Уявіть, що ви володієте ресторанчиком і відстежуєте, чи є продукти: помідори, цибуля, часник, спеції і т. д. Якщо у вас кілька списків із вмістом холодильників, то вам доведеться оновлювати їх усі, коли ви готуєте якусь страву. А якщо список один, то і вносити зміни доведеться лише до нього.

Найчастіше дублюючий код виникає тому, що ви робите дві речі чи більше, які мають багато спільного. Але невелика різниця між ними змушує вас писати кілька функцій, і ті здебільшого роблять те саме. Видалення дублюючого коду означає, що ви створюєте абстракцію, яка може обробляти всі відмінності за допомогою єдиної функції/модуля/класу.

Правильний вибір абстракції критично важливий, тому слід дотримуватися принципів SOLID, описаних у розділі "[Класи](#Класи)". Погані абстракції можуть виявитися гіршими за дублюючий код, тому будьте обережні! Але якщо можете написати гарно, то робіть це! Не повторюйтесь, інакше виявиться, що при кожній зміні вам потрібно оновлювати код у кількох місцях.

**Погано:**

```php
function showDeveloperList(array $developers): void
{
    foreach ($developers as $developer) {
        $expectedSalary = $developer->calculateExpectedSalary();
        $experience = $developer->getExperience();
        $githubLink = $developer->getGithubLink();
        $data = [
            $expectedSalary,
            $experience,
            $githubLink
        ];

        render($data);
    }
}

function showManagerList(array $managers): void
{
    foreach ($managers as $manager) {
        $expectedSalary = $manager->calculateExpectedSalary();
        $experience = $manager->getExperience();
        $githubLink = $manager->getGithubLink();
        $data = [
            $expectedSalary,
            $experience,
            $githubLink
        ];

        render($data);
    }
}
```

**Гарно:**

```php
function showList(array $employees): void
{
    foreach ($employees as $employee) {
        $expectedSalary = $employee->calculateExpectedSalary();
        $experience = $employee->getExperience();
        $githubLink = $employee->getGithubLink();
        $data = [
            $expectedSalary,
            $experience,
            $githubLink
        ];

        render($data);
    }
}
```

**Дуже гарно:**

Найкраще використовувати компактну версію коду.

```php
function showList(array $employees): void
{
    foreach ($employees as $employee) {
        render([
            $employee->calculateExpectedSalary(),
            $employee->getExperience(),
            $employee->getGithubLink()
        ]);
    }
}
```

**[⬆ повернутися до змісту](#Зміст)**

## Переклади

На іших мовах:

- :uk: **Англійська:**
  - [jupeter/clean-code-php](https://github.com/jupeter/clean-code-php)
- :cn: **Китайська:**
  - [php-cpm/clean-code-php](https://github.com/php-cpm/clean-code-php)
- :ru: **Російська:**
  - [peter-gribanov/clean-code-php](https://github.com/peter-gribanov/clean-code-php)
- :es: **Іспанська:**
  - [fikoborquez/clean-code-php](https://github.com/fikoborquez/clean-code-php)
- :brazil: **Португальська:**
  - [fabioars/clean-code-php](https://github.com/fabioars/clean-code-php)
  - [jeanjar/clean-code-php](https://github.com/jeanjar/clean-code-php/tree/pt-br)
- :thailand: **Тайська:**
  - [panuwizzle/clean-code-php](https://github.com/panuwizzle/clean-code-php)
- :fr: **Французька:**
  - [errorname/clean-code-php](https://github.com/errorname/clean-code-php)
- :vietnam: **В'єтнамська:**
  - [viethuongdev/clean-code-php](https://github.com/viethuongdev/clean-code-php)
- :kr: **Корейська:**
  - [yujineeee/clean-code-php](https://github.com/yujineeee/clean-code-php)
- :tr: **Турецька:**
  - [anilozmen/clean-code-php](https://github.com/anilozmen/clean-code-php)
- :iran: **Персидська:**
  - [amirshnll/clean-code-php](https://github.com/amirshnll/clean-code-php)
- :bangladesh: **Бенгальська:**
  - [nayeemdev/clean-code-php](https://github.com/nayeemdev/clean-code-php)
- :egypt: **Арабська:**
  - [ahmedalmory/clean-code-php](https://github.com/ahmedalmory/clean-code-php)
- :jp: **Японська:**
  - [hayato07/clean-code-php](https://github.com/hayato07/clean-code-php)
- :uk: **Українська**
  - [astropsy999/clean-code-php](https://github.com/astropsy999/clean-code-php)

**[⬆ повернутися до змісту](#Зміст)**
