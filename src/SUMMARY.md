# Мова програмування Rust

[Мова програмування Rust](title-page.md)
[Передмова](foreword.md)
[Вступ](ch00-00-introduction.md)

## Початок

- [Початок](ch01-00-getting-started.md)
    - [Встановлення](ch01-01-installation.md)
    - [Привіт, світ!](ch01-02-hello-world.md)
    - [Привіт, Cargo!](ch01-03-hello-cargo.md)

- [Програмування гри "Вгадай число"](ch02-00-guessing-game-tutorial.md)

- [Загальні концепції програмування](ch03-00-common-programming-concepts.md)
    - [Змінні та поняття змінності](ch03-01-variables-and-mutability.md)
    - [Типи даних](ch03-02-data-types.md)
    - [Функції](ch03-03-how-functions-work.md)
    - [Коментарі](ch03-04-comments.md)
    - [Управління виконанням коду](ch03-05-control-flow.md)

- [Розуміння власності](ch04-00-understanding-ownership.md)
    - [Що таке власність?](ch04-01-what-is-ownership.md)
    - [Посилання та Запозичення](ch04-02-references-and-borrowing.md)
    - [Зрізи](ch04-03-slices.md)

- [Використання структур для об'єднання зв'язаних даних](ch05-00-structs.md)
    - [Визначення та ініціалізація структур](ch05-01-defining-structs.md)
    - [Приклад використання структур](ch05-02-example-structs.md)
    - [Синтаксис методів](ch05-03-method-syntax.md)

- [Перерахування та Зіставлення зі зразком](ch06-00-enums.md)
    - [Визначення перерахування](ch06-01-defining-an-enum.md)
    - [Оператор управління виконанням коду `match`](ch06-02-match.md)
    - [Компактне управління виконанням коду з `if let`](ch06-03-if-let.md)

## Основи Rust

- [Управління зростаючими проектами з Пакетами, Крейтами та Модулями](ch07-00-managing-growing-projects-with-packages-crates-and-modules.md)
    - [Пакети та Крейти](ch07-01-packages-and-crates.md)
    - [Визначення модулів для інкапсуляції](ch07-02-defining-modules-to-control-scope-and-privacy.md)
    - [Шляхи для посилання на модуль у дереві модулів](ch07-03-paths-for-referring-to-an-item-in-the-module-tree.md)
    - [Введення шляхів у область визначення за допомогою ключового слова `use`](ch07-04-bringing-paths-into-scope-with-the-use-keyword.md)
    - [Розділення модулів у різні файли](ch07-05-separating-modules-into-different-files.md)

- [Поширені колекції](ch08-00-common-collections.md)
    - [Зберігання масивів даних у векторах](ch08-01-vectors.md)
    - [Зберігання UTF-8 тексту у рядках](ch08-02-strings.md)
    - [Зберігання ключів та значень у хеш-таблиці](ch08-03-hash-maps.md)

- [Обробка помилок](ch09-00-error-handling.md)
    - [Невиправні помилки з `panic!`](ch09-01-unrecoverable-errors-with-panic.md)
    - [Виправні помилки з `Result`](ch09-02-recoverable-errors-with-result.md)
    - [`panic!` або не `panic!`](ch09-03-to-panic-or-not-to-panic.md)

- [Дженерики, Трейти та Лайфтайми](ch10-00-generics.md)
    - [Дженерики](ch10-01-syntax.md)
    - [Трейти: Визначення спільної поведінки](ch10-02-traits.md)
    - [Перевірка посилань за допомогою Лайфтаймів](ch10-03-lifetime-syntax.md)

- [Написання автоматизованих тестів](ch11-00-testing.md)
    - [Як писати тести](ch11-01-writing-tests.md)
    - [Контроль за виконанням тестів](ch11-02-running-tests.md)
    - [Організація тестування](ch11-03-test-organization.md)

- [Розробка CLI](ch12-00-an-io-project.md)
    - [Приймання аргументів командного рядка](ch12-01-accepting-command-line-arguments.md)
    - [Читання файлу](ch12-02-reading-a-file.md)
    - [Рефакторинг для покращення модульності та обробка помилок](ch12-03-improving-error-handling-and-modularity.md)
    - [Розвиток функціональності бібліотеки за допомогою TDD](ch12-04-testing-the-librarys-functionality.md)
    - [Робота зі змінними середовища](ch12-05-working-with-environment-variables.md)
    - [Запис повідомлень про помилки до `stderr` замість `stdout`](ch12-06-writing-to-stderr-instead-of-stdout.md)

## Думай на Rust

- [Функціональні особливості мови: Ітератори та Замикання](ch13-00-functional-features.md)
    - [Замикання: Анонімні функції, які можуть замикати їхнє середовище](ch13-01-closures.md)
    - [Обробка елементів за допомогою ітераторів](ch13-02-iterators.md)
    - [Покращення нашого CLI проекту](ch13-03-improving-our-io-project.md)
    - [Порівняння продуктивності: Цикли проти Ітераторів](ch13-04-performance.md)

- [Більше про Cargo та Crates.io](ch14-00-more-about-cargo.md)
    - [Налаштування збірок за допомогою Release профілів](ch14-01-release-profiles.md)
    - [Публікація Крейту до Crates.io](ch14-02-publishing-to-crates-io.md)
    - [Cargo Workspaces](ch14-03-cargo-workspaces.md)
    - [Встановлення Бінарників з Crates.io з `cargo install`](ch14-04-installing-binaries.md)
    - [Розширення Cargo за допомогою кастомних команд](ch14-05-extending-cargo.md)

- [Розумні Покажчики](ch15-00-smart-pointers.md)
    - [Використання `Box <T>` для вказування на дані у купі](ch15-01-box.md)
    - [Обробка розумних покажчиків як звичайних посилань з трейтом `Deref`](ch15-02-deref.md)
    - [Запуск коду після деініціалізації з трейтом `Drop`](ch15-03-drop.md)
    - [`Rc <T>`, розумний покажчик, що рахує посилання](ch15-04-rc.md)
    - [`RefCell<T>` і паттерн внутрішньої мутації](ch15-05-interior-mutability.md)
    - [Цикли посилань можуть призвести до витікання пам'яті](ch15-06-reference-cycles.md)

- [Безстрашна паралельність](ch16-00-concurrency.md)
    - [Використання потоків для одночасного запуску коду](ch16-01-threads.md)
    - [Використання канали для передачі даних між потоками](ch16-02-message-passing.md)
    - [Паралельність з діленням стану](ch16-03-shared-state.md)
    - [Розширна паралельність з Трейтами `Sync` та `Send`](ch16-04-extensible-concurrency-sync-and-send.md)

- [Об'єктно Орієнтоване Програмування на Rust](ch17-00-oop.md)
    - [Характеристика об'єктно-орієнтованих мов](ch17-01-what-is-oo.md)
    - [Використання Трейт-Об'єктів, які дозволяють значення різних типів](ch17-02-trait-objects.md)
    - [Реалізація об’єктно-орієнтованого шаблону проектування](ch17-03-oo-design-patterns.md)

## Просунуті теми

- [Шаблони та відповідність](ch18-00-patterns.md)
    - [Усі місця, де можуть використовуватись шаблони](ch18-01-all-the-places-for-patterns.md)
    - [Спростування: Чи може шаблон не мати відповідність](ch18-02-refutability.md)
    - [Синтаксис шаблонів](ch18-03-pattern-syntax.md)

- [Просунуті функції](ch19-00-advanced-features.md)
    - [Небезпечний Rust](ch19-01-unsafe-rust.md)
    - [Просунуті Трейти](ch19-03-advanced-traits.md)
    - [Просунуті Типи](ch19-04-advanced-types.md)
    - [Просунуті Функції та Замикання](ch19-05-advanced-functions-and-closures.md)
    - [Макроси](ch19-06-macros.md)

- [Фінальний проект: Створення багатопотокового веб-сервера](ch20-00-final-project-a-web-server.md)
    - [Створення однопотокового веб-сервера](ch20-01-single-threaded.md)
    - [Перетворення нашого однопотокового сервера в багатопотоковий](ch20-02-multithreaded.md)
    - [Витончене завершення роботи та очищення](ch20-03-graceful-shutdown-and-cleanup.md)

- [Додаток](appendix-00.md)
    - [A - Ключові слова](appendix-01-keywords.md)
    - [B - Оператори та Символи](appendix-02-operators.md)
    - [C - Похідні Трейти](appendix-03-derivable-traits.md)
    - [D - Корисні інструменти розробки](appendix-04-useful-development-tools.md)
    - [E - Видання](appendix-05-editions.md)
    - [F - Переклади Книги](appendix-06-translation.md)
    - [G - Як робиться Rust та "Nightly Rust"](appendix-07-nightly-rust.md)
