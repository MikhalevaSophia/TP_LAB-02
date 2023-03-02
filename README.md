## Homework

### Part I

1. Создайте пустой репозиторий на сервисе github.com (или gitlab.com, или bitbucket.com).
2. Выполните инструкцию по созданию первого коммита на странице репозитория, созданного на предыдещем шаге.

> Создаём директорию для лабы и открываем терминал в ней.
> 
> ```
> $ echo "# TP-lab02" >> README.md
> $ git init
> $ git add README.md
> $ git commit -m "first commit"
> $ git branch -M main
> $ git remote add origin https://github.com/<user>/TP-lab02.git
> $ git push -u origin main
> ```

3. Создайте файл `hello_world.cpp` в локальной копии репозитория (который должен был появиться на шаге 2). Реализуйте программу **Hello world** на языке C++ используя плохой стиль кода. Например, после заголовочных файлов вставьте строку `using namespace std;`.

> Создаём файл hello_world.cpp. В него пишем:
> ```cpp
> include <iostream>
> using namespace std;
> int main() {
> cout << "Hello world!";
> }
> ```

4. Добавьте этот файл в локальную копию репозитория.

> ```sh
> $ git add hello_world.cpp
> ```

5. Закоммитьте изменения с *осмысленным* сообщением.

> ```sh
> $ git commit -m "added hello_world.cpp"
> ```

6. Изменитьте исходный код так, чтобы программа через стандартный поток ввода запрашивалось имя пользователя. А в стандартный поток вывода печаталось сообщение `Hello world from @name`, где `@name` имя пользователя.

> В файле hello_world.cpp:
> ```cpp
> include <iostream>
> include <string>
> using namespace std;
> int main() {
> cout << "Hello world!";
> string name;
> cout << "Please enter name";
> cin >> name;
> cout << "Hello world from " << name;
> }
> ```

7. Закоммитьте новую версию программы.

> ```sh
> $ git add hello_world.cpp
> $ git commit -m "updated hello_world.cpp to ask for name"
> ```

8. Запуште изменения в удалёный репозиторий.

> ```sh
> $ git push origin main
> ```

9. Проверьте, что история коммитов доступна в удалёный репозитории.

> Просто заходим на гитхаб и смотрим что появилось два коммита.

### Part II

1. В локальной копии репозитория создайте локальную ветку `patch1`.

> ```sh
> $ git branch patch1
> $ git checkout patch1
> ```

2. Внесите изменения в ветке `patch1` по исправлению кода и избавления от `using namespace std;`.

> В файле hello_world.cpp:
> ```cpp
> include <iostream>
> include <string>
> int main() {
> std::string name;
> std::cout << "Please enter name";
> std::cin >> name;
> std::cout << "Hello world from " << name;
> }
> ```
>

3. **commit**, **push** локальную ветку в удалённый репозиторий.

> ```sh
> $ git add hello_world.cpp
> $ git commit -m "patched hello_world.cpp"
> $ git push origin patch1
> ```

4. Проверьте, что ветка `patch1` доступна в удалёный репозитории.

5. Создайте pull-request `patch1 -> master`.

6. В локальной копии в ветке `patch1` добавьте в исходный код комментарии.

> В файле hello_world.cpp:
> ```cpp
> include <iostream>
> include <string>
> int main() {
> std::string name;
> // Бабушка технарь, дед гуманитарий
> std::cout << "Please enter name";
> std::cin >> name;
> std::cout << "Hello world from " << name;
> }
> ```

7. **commit**, **push**.

> ```sh
> $ git add hello_world.cpp
> $ git commit -m "added comment"
> $ git push origin patch1
> ```

8. Проверьте, что новые изменения есть в созданном на **шаге 5** pull-request

9. В удалённый репозитории выполните  слияние PR `patch1 -> master` и удалите ветку `patch1` в удаленном репозитории.

10. Локально выполните **pull**.

> ```sh
> $ git checkout main
> $ git pull origin main
> ```

11. С помощью команды **git log** просмотрите историю в локальной версии ветки `master`.

> ```sh
> $ git log
> ```

12. Удалите локальную ветку `patch1`.

> ```sh
> $ git branch -d patch1
> ```

### Part III

1. Создайте новую локальную ветку `patch2`.

> ```sh
> $ git branch patch2
> $ git checkout branch2
> ```

2. Измените *code style* с помощью утилиты [**clang-format**](http://clang.llvm.org/docs/ClangFormat.html). Например, используя опцию `-style=Mozilla`.

> ```sh
> $ sudo apt install clang-format
> $ clang-format hello_world.cpp -style=Mozilla -i hello_world.cpp
> ```

3. **commit**, **push**, создайте pull-request `patch2 -> master`.

> ```sh
> $ git add hello_world.cpp
> $ git commit -m "changed codestyle"
> $ git push origin patch2
> ```
>

4. В ветке **master** в удаленном репозитории измените комментарии, например, расставьте знаки препинания, переведите комментарии на другой язык.


5. Убедитесь, что в pull-request появились *конфликтны*.

6. Для этого локально выполните **pull** + **rebase** (точную последовательность команд, следует узнать самостоятельно). **Исправьте конфликты**.

> ```sh
> $ git pull origin main --rebase
> ```

7. Сделайте *force push* в ветку `patch2`

> **force-push** полностью перезаписывает историю ветки
>
> ```sh
> $ git push -f origin patch2
> ```

8. Убедитель, что в pull-request пропали конфликтны. 
9. Вмержите pull-request `patch2 -> master`.


## Links

- [hub](https://hub.github.com/)
- [GitHub](https://github.com)
- [Bitbucket](https://bitbucket.org)
- [Gitlab](https://about.gitlab.com)
- [LearnGitBranching](http://learngitbranching.js.org/)
