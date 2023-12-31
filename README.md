# Описание:
Итоговый проект курса ["Автоматизация тестирования с помощью Selenium и Python"](https://stepik.org/course/575).

# Установка окружения и запуск:
<details>
  <summary>Инструкция</summary>
  
- Установите Python3. Для этого на [официальной странице](https://www.python.org/downloads/windows/)  Python выберите стабильную версию для Windows, и скачайте файл для вашей системы (64-разрядная или 32-разрядная). Во время установки убедитесь в том, что вы поставили галочку в разделе `Add Python 3.x to PATH`.
Чтобы проверить правильность установки, откройте командную строку  Windows (Пуск - Найти программу - cmd.exe и Запустить). В консоли  введите python --version (на некоторых сборках Windows нужно вводить  короткую команду, например, py --version):
```
python --version
Python 3.10.11
```
- Создайте папку, где будут храниться наши виртуальные окружения, и перейдите в неё:
```
mkdir environments
cd environments
```
Создадим виртуальное окружение:
```
py -m venv selenium_env
```
- Запустим созданный для нас приложением venv файл activate.bat, чтобы активировать окружение:
```
selenium_env\Scripts\activate.bat
```
- Клонируйте репозиторий. В папке `environments` выполните:
```
git clone https://github.com/HappyClickClack/stepik_auto_tests_course_final_project
```
(_GIT client for win_: https://git-scm.com/download/win)
  
- Установите зависимости. В виртуальном окружении выполните:
```
cd stepik_auto_tests_course_final_project
pip install -r requirements.txt
```

- Установите драйвер для браузера: Windows. Для этого откройте сайт https://sites.google.com/chromium.org/driver/ (старая версия сайта https://sites.google.com/a/chromium.org/chromedriver/downloads)  и скачайте ту версию ChromeDriver, которая соответствует версии вашего  браузера. Чтобы узнать версию браузера, откройте новое окно в Chrome, в  поисковой строке наберите: chrome://version/ и нажмите Enter. В верхней  строчке вы увидите информацию про версию браузера. Разархивируйте скачанный файл. Создайте в папке `environments` (см выше) папку chromedriver и положите разархивированный ранее файл chromedriver.exe.
Добавьте в системную переменную PATH путь к chromedriver. Как это сделать в разных версиях Windows, описано здесь: https://www.computerhope.com/issues/ch000549.htm. 
Или можно прописать путь к драйверу в скрипте (не реализовано в этом репо.):
```
webdriver.Chrome(<путь к драйверу>)
```
- Запустите тесты. В виртуальном окружении выполните:
```
pytest -v -s  
```
  
</details>

# Структура репозитория:

/helper/:
- `utility.py` - вспомогательные методы.

/pages/:
- `locators.py` - локаторы каждой отдельной страницы завёрнуты в класс, чтобы было удобно импортировать;
- `base_page.py` - методы, которые применяются по всему проекту вообще, всё завернуто в класс;
- `basket_page.py` - методы для страницы Корзины, всё завернуто в класс;
- `login_page.p`y - методы для страницы авторизации;
- `main_page.py` - методы домашней страницы;
- `product_page.py` - методы продуктовой страницы.

/:
- `__init__.py` - это файл для того, чтобы мы могли выполнять import внутри проекта;
- `conftest.p`y - фикстуры и путь к Firefox (`firefox_binary_path`) для корректной работы драйвера;
- `pytest.ini` - зарегистрированные метки;
- `requirements.txt` - внешние зависимости;
- `test_main_page.py` - тесты для главной страницы;
- `test_product_page.py` - тесты для страницы товара.
