lab2 Lotnik Vladislav IU8-23
Part I
Создайте пустой репозиторий на сервисе github.com.
    $ git config --global user.name "vlad-192"
    >
    $ git config --global user.email "vladlotnik825@gmail.com"
    >
    $ git clone https://github.com/vlad-192/lab02.git
    > Cloning into 'lab02'...

Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдущем шаге.
    $ cd lab02
    >
    $ git add .
    >
    $ git commit -m "added sources"
    > [main] added sources
    $ git push origin main
    > To https://github.com/vlad-192/lab02.git
    > main -> main

Создайте файл hello_world.cpp в локальной копии репозитория. Реализуйте программу Hello world на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку using namespace std;
    $ nano hello_world.cpp

```cpp
#include <iostream>
using namespace std;

int main()
{
    cout << "Hello world" << endl;
    return 0;
}
```
Добавьте этот файл в локальную копию репозитория.
    $ git add hello_world.cpp
    >

Закоммитьте изменения с осмысленным сообщением.
    $ git commit -m "added hello world program"
    > 1 file changed, 7 insertions(+)
    > create mode 100644 hello_world.cpp
    $ git push origin main
    > To https://github.com/vlad-192/lab02.git
    > main -> main

Изменить исходный код так, чтобы программа через стандартный поток ввода запрашивала имя пользователя. А в стандартный поток вывода печаталось сообщение Hello world from @name, где @name имя пользователя.
    $ nano hello_world.cpp

```cpp
#include <iostream>
using namespace std;

int main()
{
    string name;
    cout << "Enter name: ";
    cin >> name;
    cout << "Hello world from @" << name << endl;
    return 0;
}
```
Закоммитьте новую версию программы.
    $ git add hello_world.cpp
    >
    $ git commit -m "updated hello world with username input"
    > 1 file changed

Запушьте изменения в удаленный репозиторий.
    $ git push origin main
    > To https://github.com/vlad-192/lab02.git
    > main -> main

Проверьте, что история коммитов доступна в удалённом репозитории.
    $ git log --oneline
    > updated hello world with username input
    > added hello world program
    > added sources

Part II
В локальной копии репозитория создайте локальную ветку patch1.
    $ git checkout -b patch1
    > Switched to a new branch 'patch1'

Внесите изменения в ветке patch1 по исправлению кода и избавления от using namespace std.
    $ nano hello_world.cpp
    >
    $ git add hello_world.cpp
    >

```cpp
#include <iostream>
#include <string>

int main()
{
    std::string name;
    std::cout << "Enter name: ";
    std::cin >> name;
    std::cout << "Hello world from @" << name << std::endl;
    return 0;
}
```
commit, push локальную ветку в удалённый репозиторий.
    $ git commit -m "fixed code style"
    > 1 file changed
    $ git push -u origin patch1
    > remote:
    > remote: Create a pull request for 'patch1' on GitHub by visiting:
    > remote:      https://github.com/vlad-192/lab02/pull/new/patch1
    > To https://github.com/vlad-192/lab02.git
    > * [new branch]      patch1 -> patch1
    > branch 'patch1' set up to track 'origin/patch1'.

Проверьте, что ветка patch1 доступна в удалённом репозитории.
    $ git branch -a
    > main
    > * patch1
    > remotes/origin/main
    > remotes/origin/patch1

Создайте pull-request patch1 → main.
    > действия выполнены на github

В локальной копии в ветке patch1 добавьте в исходный код комментарии.
    $ nano hello_world.cpp
    >

```cpp
#include <iostream>
#include <string>

int main()
{
    // Read username from standard input
    std::string name;
    std::cout << "Enter name: ";
    std::cin >> name;

    // Print greeting message
    std::cout << "Hello world from @" << name << std::endl;
    return 0;
}
```
commit, push.
    $ git add hello_world.cpp
    >
    $ git commit -m "added comments"
    > 1 file changed
    $ git push
    > To https://github.com/vlad-192/lab02.git
    > patch1 -> patch1

Проверьте, что новые изменения есть в созданном на шаге 5 pull-request.
    > действия выполнены на github

В удалённом репозитории выполните слияние PR patch1 -> main и удалите ветку patch1 в удаленном репозитории.
    > действия выполнены на github

Локально выполните pull.
    $ git checkout main
    > Switched to branch 'main'
    $ git pull origin main
    > Updating
    > Fast-forward
    > hello_world.cpp | changed

С помощью команды git log просмотрите историю в локальной версии ветки main.
    $ git log --oneline
    > Merge pull request from patch1
    > added comments
    > fixed code style
    > updated hello world with username input
    > added hello world program
    > added sources

Удалите локальную ветку patch1.
    $ git branch -d patch1
    > Deleted branch patch1

Part III
Создайте новую локальную ветку patch2.
    $ git checkout -b patch2
    > Switched to a new branch 'patch2'

Изменение code style с помощью утилиты clang-format. Например, используя опцию -style=Mozilla.
    $ clang-format -style=Mozilla -i hello_world.cpp
    >
    $ git add hello_world.cpp
    >

commit, push, создайте pull-request patch2 → main.
    $ git commit -m "formatted code with clang-format"
    > 1 file changed
    $ git push -u origin patch2
    > remote:
    > remote: Create a pull request for 'patch2' on GitHub by visiting:
    > remote:      https://github.com/vlad-192/lab02/pull/new/patch2
    > To https://github.com/vlad-192/lab02.git
    > * [new branch]      patch2 -> patch2
    > branch 'patch2' set up to track 'origin/patch2'.

В ветке main в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.
    > действия выполнены на github

Убедитесь, что в pull-request появились конфликты.
    > действия выполнены на github

Для этого локально выполните pull + rebase. Исправьте конфликты.
    $ git checkout patch2
    >
    $ git fetch origin
    >
    $ git rebase origin/main
    >
    $ nano hello_world.cpp
    >
    $ git add hello_world.cpp
    >
    $ git rebase --continue
    >

Сделайте force push в ветку patch2.
    $ git push --force origin patch2
    > To https://github.com/vlad-192/lab02.git
    > patch2 -> patch2

Убедитесь, что в pull-request пропали конфликты.
    > действия выполнены на github

Вмержите pull-request patch2 → main.
    > действия выполнены на github

Локально выполните pull и удалите ветку patch2.
    $ git checkout main
    > Switched to branch 'main'
    $ git pull origin main
    > Fast-forward
    $ git branch -d patch2
    > Deleted branch patch2

Result
Repository: https://github.com/vlad-192/lab02
