## Привіт, світ!

Отже, коли Rust вже встановлений можна приступати до написання вашої першої програми. Загальна традиція при вивченні нової мови програмування - писати маленьку програму яка друкує в рядку виводу "Hello, world!". Давайте зробимо те ж саме.

> Зверніть увагу: дана книга має на увазі, що читач повинен бути знайомий з 
> командним рядком. Однак, Rust не висуває будь-яких спеціальних вимог до того, 
> як ви пишете і за яким принципом зберігайте код своїх програм. З цього, якщо
> ви віддаєте перевагу використовувати інтегроване середовище розробки (IDE) 
> замість командного рядка терміналу, відчувайте себе спокійно і користуйтеся 
> тим, чим вам зручно. Різні IDE мають різний рівень підтримки Rust, тому не
> забувайте перевіряти документацію до обраної IDE. Однак, не так давно команда
> Rust сфокусувалася на завданні більшої підтримки мови в різних IDE і 
> однозначно зробила певний прогрес в цьому напрямі!

### Створення папки проекту

Перш за все почнемо з створення директорії, в якій будемо зберігати наш код на мові Rust. Насправді не важливо, де зберігати наш код. Однак, для вправ і проектів, що обговорюються в цій книзі, ми радимо створити директорію *projects* в вашому домашньому каталозі, там же і зберігати в майбутньому код програм з книги.

Відкрийте термінал і введіть наступні команди для того, щоб створити директорію *projects* для зберігання коду різних проектів, і, всередині неї, директорію *hello_world* для проекту "Hello, world!".

Для Linux, macOS і PowerShell на Windows, введіть:

```console
$ mkdir ~/projects
$ cd ~/projects
$ mkdir hello_world
$ cd hello_world
```

Для Windows в CMD, введіть:

```cmd
> mkdir "%USERPROFILE%\projects"
> cd /d "%USERPROFILE%\projects"
> mkdir hello_world
> cd hello_world
```

### Написання та запуск першої Rust програми

Тепер створимо новий файл, в якому збережемо вихідний код програми, назвемо його *main.rs*. Зауважте, що файли з кодом на мові програмування Rust завжди закінчуються розширенням .rs. У разі, якщо ви захочете використовувати більш одного слова в назві файлу, використовуйте знак підкреслення як роздільник. Наприклад, можливо використовувати іменування *hello_world.rs*, але не рекомендується використовувати варіант *helloworld.rs*.

Тепер відкриємо файл main.rs для редагування і введемо наступні рядки коду:

<span class="filename">Назва файлу: main.rs</span>

```rust
fn main() {
    println!("Hello, world!");
}
```

<span class="caption">Лістинг 1-1: Програма яка друкує `Hello, world!`</span>

Збережіть файл і поверніться назад у вікно терміналу, щоб скомпілювати і запустити нашу першу програму. На Linux або macOS для цього введіть наступні команди:

```console
$ rustc main.rs
$ ./main
Hello, world!
```

У Windows, введіть команду. `\main.exe` замість `./main`:

```powershell
> rustc main.rs
> .\main.exe
Hello, world!
```

Незалежно від операційної системи, рядок `Hello, world!` повинен друкуватися у вікні вашого терміналу. Якщо ви не побачили виведення, поверніться до частини ["Вирішення проблем"][troubleshooting]<!-- ignore --> розділу "Встановлення" для отримання допомоги.

Якщо надрукувалося `Hello, world!`, то прийміть наші вітання! Ви написали програму на Rust, що робить вас Rust програмістом - ласкаво просимо!

### Анатомія програми на Rust

Давайте розглянемо в деталях, що відбувається в програмі "Hello, world!". Ось перший шматок пазла:

```rust
fn main() {

}
```

Ці рядки визначають функцію в Rust. Функція `main` має спеціальний сенс: вона завжди є першим кодом, який запускається в виконуваній програмі на Rust. Перший рядок оголошує функцію з ім'ям `main` у якій немає параметрів і вона нічого не повертає. Якби тут були параметри, вони були б записані всередині круглих дужок, `()`.

Також зауважимо, що тіло функції обгорнуті в фігурні дужки `{}` (curly brackets). У Rust тіло будь-якої функції обертається в фігурні дужки. Хорошим стилем є розміщення відкриваючої дужки в рядку оголошення функції, залишаючи пробіл між ними.

На момент написання цих рядків інструмент, який виконує автоматичне форматування, називається `rustfmt` і знаходиться ще в розробці. Якщо ви хочете використовувати стандартний стиль у всіх Rust проектах, то `rustfmt` відформатує код в потрібному стилі. Команда Rust планує включити даний інструмент в стандартний дистрибутив Rust, подібно `rustc` компілятору. Так що в залежності від того, коли ви читаєте цю книгу, `rustfmt` вже може бути інстальований на ваш комп'ютер! Загляньте в документацію для деталей.

Вміст функції `main`:

```rust
    println!("Hello, world!");
```

Цей рядок робить всю роботу в цій маленькій програмі: друкує текст на екран. Можна помітити чотири важливі деталі.

Перша, не настільки помітна, - в стилі Rust для відступу використовуються чотири пробіли, а не знак табуляції.

По-друге, `println!` викликає макрос Rust. Якби замість цього він викликав функцію, вона вводилася б як `println` (без!). Ми обговоримо макроси Rust більш докладно в 19-му розділі. На даний момент вам просто потрібно знати, що використання `!` означає, що ви викликаєте макрос замість звичайної функції, і що макроси не завжди дотримуються тих же самих правил, що і функції.

Третя - ви бачите рядок `"Hello, world!"`. Ми передаємо цей рядок як аргумент в макрос `println!` і, завдяки цьому, рядок виводиться макросом на екран.

Четверта - в кінці рядка стоїть крапка з комою (`;`), яка означає, що вираз закінчився і наступний вираз можна починати знову. Велика частина рядків у Rust коді закінчується крапкою з комою.

### Компіляція і виконання коду є окремими кроками

Тільки що ви запустили новостворену програму, тепер вивчимо кожен крок цього процесу.

Перед запуском програми, її необхідно скомпілювати компілятором Rust за допомогою введення команди `rustc` і передачі імені вашого файлу з вихідним кодом, наприклад так:

```console
$ rustc main.rs
```

Якщо ви знайомі з C або C++, то помітили, що це дуже схоже на виклик компіляції за допомогою `gcc` або `clang`. Після успішної компіляції, Rust видасть двійковий виконуваний файл.

Для того, щоб подивитися на виконуваний файл на Linux, macOS і в PowerShell на Windows досить виконати команду ls в командному рядку. На Linux або macOS буде відображено два файли. У PowerShell на Windows, як і в Windows CMD - три файли.

```console
$ ls
main  main.rs
```

У CMD на Windows слід ввести наступні команди:

```cmd
> dir /B %= the /B option says to only show the file names =%
main.exe
main.pdb
main.rs
```

В обох випадках видно: файл вихідного коду з розширенням *.rs*, виконуваний двійковий файл (*main.exe* в Windows, але *main* на всіх інших платформах), а у випадку використання Windows, ще й файл, який включає відлагоджувальну інформацію з розширенням *.pdb*. Звідси ми можемо запустити нашу програму (виконуваний двійковий файл) *main* або *main.exe* відповідної командою для Windows чи інших ОС:

```console
$ ./main # or .\main.exe on Windows
```

Якщо *main.rs* був з текстом "Hello, world!", То рядок `Hello, world` буде надрукована в терміналі.

Якщо ви знайомі з динамічними мовами на зразок Ruby, Python або JavaScript, то, можливо, вам не доводилося виконувати компіляцію і запуск програми окремими кроками. Rust є "заздалегідь скомпільованою" (`ahead-of-time compiled`) мовою. Це означає, що можна скомпілювати програму і передати виконуваний файл ще комусь, і одержувачі зможуть його запустити, не маючи локально встановленого Rust. А якщо ви віддаєте файл `.rb`, `.py` або `.js`, то одержувачам необхідно мати встановлену реалізацію для Ruby, Python або JavaScript відповідно. Але в цих мовах потрібна тільки одна команда для компіляції і запуску програми. Що ж, все є компромісом в дизайні мов.

Проста компіляція з допомогою `rustc` підходить тільки для простих програм, але коли ваші проекти стають складніше, ви захочете керувати всіма опціями і спростити обмін своїм кодом з іншими. Далі ми представимо інструмент Cargo, який допоможе в написанні справжніх, а значить і більш складних, програм на Rust.

[troubleshooting]: ch01-01-installation.html#troubleshooting
