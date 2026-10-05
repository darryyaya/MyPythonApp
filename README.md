# my-python-app

Учебный проект с CI на GitHub Actions для Python-приложения.

## 📌 Цель работы

Настроить CI для Python-проекта с автоматической проверкой кода, тестами и сборкой Docker-образа.

## 🎯 Что делает CI

При каждом push/PR автоматически:

- **Линтинг** (flake8) — проверка кода на ошибки
- **Тесты** (pytest) — запуск unit-тестов
- **Сборка Docker-образа** — без публикации

## 📂 Структура проекта

```
my-python-app/
├── .github/
│   └── workflows/
│       └── ci.yml            # GitHub Actions workflow
├── myapp/
│   ├── __init__.py
│   └── app.py                # основной код
├── tests/
│   └── test_app.py           # тесты (pytest)
├── requirements.txt          # зависимости
├── setup.py
├── Dockerfile
└── README.md
```

## 🐍 Основной код

```python
def add(a: int, b: int) -> int:
    """Возвращает сумму двух чисел."""
    return a + b

def main():
    print("Hello from my Python app!")

if __name__ == "__main__":
    main()
```

## 🚀 Запуск локально

### Через Docker (рекомендуется)

```bash
docker build -t my-python-app:test .
docker run --rm my-python-app:test
```

### Без Docker (нужен Python 3.9+)

```bash
pip install -r requirements.txt
pip install -e .
pytest tests/
python myapp/app.py
```

## 📸 Результат запуска

Ниже — вывод приложения в терминале после сборки и запуска Docker-контейнера:

![Вывод приложения в терминале](/img/terminal.png)

```
Hello from my Python app!
```

## ⚙️ CI Workflow

Workflow запускается на **4 версиях Python** (3.9, 3.10, 3.11, 3.12) параллельно:

- Python 3.9
- Python 3.10
- Python 3.11
- Python 3.12

После успешных тестов запускается job сборки Docker-образа.

## ✅ Результат

При каждом push в ветку `main` запускается CI.
На вкладке **Actions** отображаются 🟢 зелёные галочки — все проверки пройдены успешно.

**Ссылка на Actions:**  
https://github.com/xem1zo/my-python-app/actions

## 📝 Вывод

В ходе работы я освоил:

- Настройку CI для Python-проектов в GitHub Actions
- Использование matrix strategy для тестирования на нескольких версиях Python
- Линтинг кода через flake8
- Тестирование через pytest
- Сборку Docker-образа в CI без публикации
