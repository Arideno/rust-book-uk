## Привіт, Cargo!

Cargo - це система збирання і менеджер пакетів Rust. Велика частина розробників використовують даний інструмент для управління проектами, тому що Cargo виконує за вас безліч завдань, таких як збірка коду, завантаження бібліотек, від яких залежить ваш код, і створення цих бібліотек. (Ми називаємо бібліотеки, які потрібні вашому коду, *залежностями*.)

Найпростіші Rust програми, на кшталт тієї, що ми вже написали, не мають залежностей. Якби ми зібрали "Hello, world!" проект за допомогою Cargo, то збірка використовувала б частину можливостей Cargo: ті її функції, які виконують лише збирання коду. Як ви будете писати складніші програми на Rust, ви будете додавати в них різні залежності. Якщо ви почнете проект з використанням Cargo, то додавати залежності буде набагато простіше, ніж без нього.

Оскільки велика частина проектів використовує Cargo, то інша частина книги має на увазі, що ви також використовуєте Cargo. Cargo встановлюється разом з Rust при використанні офіційних програм для встановлення, обговорюваних в розділі ["Встановлення"][installation]. Якщо ви встановили Rust іншим способом, то перевірте, чи працює він, ввівши команду перевірки версії Cargo в терміналі:

```console
$ cargo --version
```

Якщо команда видала номер версії, то значить Cargo встановлений. Якщо ви бачите помилку, як `command not found ("команда не знайдена")`, подивіться в документацію для використаного вами способу встановлення, щоб виконати встановлення Cargo окремо.

### Створення проекту за допомогою Cargo

Давайте створимо новий проект за допомогою Cargo і подивимося, як він відрізняється від нашого початкового проекту "Hello, world!". Перейдіть назад в папку *projects* (або будь-яку іншу, де ви вирішили зберігати код). Потім, в будь-якій операційний системі, запустіть команду:

```console
$ cargo new hello_cargo
$ cd hello_cargo
```

Перша команда створює нову папку з назвою *hello_cargo*. Ми дали назву проекту hello_cargo, тому Cargo створює свої файли всередині папки з цим ім'ям.

Перейдемо в каталог *hello_cargo* і подивимося файли. Побачимо, що Cargo згенерував два файли і одну директорію: файл Cargo.toml і каталог *src* з файлом *main.rs* всередині.

Крім того, cargo ініціалізував новий репозиторій Git разом з файлом .gitignore. Файли Git НЕ будуть згенеровані, якщо ви запустите cargo new в існуючому репозиторії Git; ви можете змінити цю поведінку, використовуючи `cargo new --vcs=git`.

> Примітка: Git - це поширена система контролю версій. Ви можете змусити `cargo 
> new` використовувати іншу систему контролю версій або взагалі відмовитися від 
> неї, використовуючи прапор `--vcs`. Запустіть `cargo new --help`, щоб побачити 
> доступні параметри.

Відкрийте файл *Cargo.toml* в будь-якому текстовому редакторі. Він повинен виглядати як код в лістингу 1-2.

<span class="filename">Назва файлу: Cargo.toml</span>

```toml
[package]
name = "hello_cargo"
version = "0.1.0"
edition = "2018"

[dependencies]
```

<span class="caption">Лістинг 1-2: Вміст файлу *Cargo.toml* згенерований командою `cargo new`</span>

Це файл у форматі [*TOML*](https://toml.io)<!-- ignore -->(*Tom's Obvious, Minimal Language*), який є форматом конфігурації Cargo.

Перший рядок, `[package]`, є головною секцією, яка вказує що наступні інструкції налаштовують пакет. При додаванні більше інформації в даний файл, буде додаватися більше секцій та інструкцій (рядків).

Наступні три рядки задають інформацію про конфігурацію, необхідну Cargo для компіляції вашої програми: ім'я, версію і видання Rust, яке буде використовуватися. Ми поговоримо про ключі `edition` в [Додатку E][appendix-e]<!-- ignore -->.

Останній рядок, `[dependencies]` є початком секції для списку будь-яких залежностей вашого проекту. У Rust, це зовнішні пакети коду, на які посилаються ключовим словом *crate*. Нам не потрібні залежності в даному проекті, але ми будемо використовувати їх в першому проекті 2-го розділу, так що нам стане в нагоді ця секція залежностей потім.

Відкрийте файл *src/main.rs* і загляньте в нього:

<span class="filename">Назва файлу: src/main.rs</span>

```rust
fn main() {
    println!("Hello, world!");
}
```

Cargo згенерував програму "Hello, world!", таку ж як ми писали в лістингу 1-1! Відмінностями між нашим попереднім проектом і проектом, який генерує Cargo є те, що Cargo поміщає вихідний код в каталог *src* і додає конфігураційний файло *Cargo.toml* в кореневій директорії нашого проекту.

Cargo очікує, що ваші вихідні файли знаходяться всередині каталогу *src*. Каталог верхнього рівня проекту призначений тільки для файлів README, інформації про ліцензії, файли конфігурації і чогось ще, що не належить до вашого коду. Використання Cargo допомагає організовувати проект. Є місце для всього і все знаходиться на своєму місці.

Якщо ви почали проект без використання Cargo, як ми робили для "Hello, world!" проекту, то можна конвертувати його в проект з використанням Cargo. Перемістіть код в підкаталог *src* і створіть відповідний файл *Cargo.toml* в папці.

### Збирання і запуск Cargo проекту

Подивимося, в чому різниця при збиранні і запуску програми "Hello, world!" за допомогою Cargo. В каталозі *hello_cargo* зберіть проект наступною командою:

```console
$ cargo build
   Compiling hello_cargo v0.1.0 (file:///projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 2.85 secs
```

Дана команда створює виконуваний файл в папці *target/debug/hello_cargo* (або *target\debug\hello_cargo.exe* на Windows), а не в поточній директорії проекту. Можна запустити виконуваний файл командою:

```console
$ ./target/debug/hello_cargo # or .\target\debug\hello_cargo.exe on Windows
Hello, world!
```

Якщо все добре, то `Hello, world!` друкується в терміналі. Запуск команди `cargo build` в перший раз також призводить до створення нового файлу *Cargo.lock* в папці верхнього рівня. Даний файл зберігає точні версії залежностей вашого проекту. Так як у нас немає залежностей, то файл порожній. Ви ніколи не повинні змінювати цей файл вручну - Cargo сам керує його вмістом для вас.

Ми тільки що зібрали проект командою `cargo build` і запустили його з `./target/debug/hello_cargo`. Але ми також можемо використовувати команду `cargo run` для компіляції коду і потім його запуску однією командою:

```console
$ cargo run
    Finished dev [unoptimized + debuginfo] target(s) in 0.0 secs
     Running `target/debug/hello_cargo`
Hello, world!
```

Зауважте, що в цей раз ви не побачили висновку про те, що Cargo компілював `hello_cargo`. Cargo зрозумів, що файли не змінювалися, тому він просто запустив вже наявний бінарний файл. Якби ви модифікували вихідний код, то Cargo зібрав би проект заново перед його запуском як ви вже бачили у консолі:

```console
$ cargo run
   Compiling hello_cargo v0.1.0 (file:///projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 0.33 secs
     Running `target/debug/hello_cargo`
Hello, world!
```

Також Cargo має команду `cargo check`. Дана команда швидко перевіряє ваш код, щоб переконатися, що він компілюється, але не створює виконуваного файлу:

```console
$ cargo check
   Checking hello_cargo v0.1.0 (file:///projects/hello_cargo)
    Finished dev [unoptimized + debuginfo] target(s) in 0.32 secs
```

У якому випадку не потрібно створювати виконуваний файл? Часто команда `cargo check` є швидшою в порівнянні з cargo build, тому що вона пропускає крок створення виконуваного файлу. У разі, якщо ви постійно перевіряєте роботу під час написання коду за допомогою `cargo check`, то це прискорює процес! Таким чином багато розробників запускають `cargo check` періодично, коли пишуть програму, щоб переконається, що вона компілюється. А запускають команду `cargo build`, коли готові створити виконуваний файл.

Повторимо отримані знання про Cargo:

* можна збирати проект, використовуючи команду `cargo build`,
* можна одночасно збирати і запускати проект однією командою `cargo run`,
* можна зібрати проект для перевірки помилок за допомогою `cargo check`, не витрачаючи час на кодогенерацію виконуваного файлу,
* cargo зберігає результати збірки не в директорію з вихідним кодом, а в окремий каталог *target/debug*.

Додатковою перевагою використання Cargo є те, що його команди однакові для різних операційних систем. З цієї точки зору, ми більше не будемо надавати окремі інструкції для Linux, macOS або Windows.

### Збірка фінальної версії (Release)

Коли проект, нарешті, готовий до релізу, можна використовувати команду `cargo build --release` для його компіляції з оптимізацією. Дана команда створює виконуваний файл в папці *target/release* на відміну від папки *target/debug*. Оптимізації роблять так, що Rust код працює швидше, але їх включення збільшує час компіляції. З цієї причини є два окремих профіля: один для розробки, коли потрібно здійснювати збірку швидко і часто, і інший, для складання фінальної програми, яку будете віддавати користувачам, яка готова до роботи і буде виконуватися максимально швидко. Якщо ви заміряє час виконання вашого коду, переконайтеся, що зібрали проект з оптимізацією `cargo build --release` і тестуєте виконуваний файл з папки *target/release*.

### Cargo як конвенція

Для простих проектів Cargo не дає великої користі у порівнянні з використанням `rustc`, але він доведе свою користь як тільки ваші програми стануть більш заплутаними. За допомогою Cargo набагато простіше координувати збірку на складних проектах, скомбіновані з безлічю зовнішніх бібліотек (crates).

Не дивлячись на те, що проект `hello_cargo` простий, тепер він використовує більшу частину реального інструментарію, який ви будете повсякденно використовувати у вашій кар'єрі, пов'язаної з Rust. Коли буде потрібно працювати над проектами розміщеними в мережі, ви зможете просто використовувати наступну послідовність команд для отримання коду за допомогою Git, переходу в каталог проекту, складання проекту:

```console
$ git clone example.org/someproject
$ cd someproject
$ cargo build
```

Для більш детальної інформації про Cargo, загляньте в [його документацію][its documentation].

[its documentation]: https://doc.rust-lang.org/cargo/

## Підсумки

Тепер ви готові почати свою подорож у Rust! У цьому розділі ви вивчили як:

* встановити останню стабільну версію Rust, використовуючи `rustup`,
* оновити Rust до останньої версії,
* відкрити локально встановлену документацію,
* написати і запустити програму типу "Hello, world!", використовуючи безпосередньо компілятор `rustc`,
* створити і запустити новий проект, використовуючи команди Cargo.

Прийшов час для створення більш змістовної програми, щоб звикнути до читання і написання коду на Rust. У розділі 2 ми створимо програму для вгадування числа. Якщо ви хочете почати з вивчення загальних концепцій програмування в Rust, загляньте в 3-й розділ, а потім поверніться до 2-го розділу.

[installation]: ch01-01-installation.html#installation
[appendix-e]: appendix-05-editions.html
