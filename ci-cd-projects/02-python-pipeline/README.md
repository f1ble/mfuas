# 02. Пайплайн для Python

Учебное Python-приложение с функцией сложения, тестами pytest и сборкой Docker-образа.

Репозиторий: [f1ble/my-python-app](https://github.com/f1ble/my-python-app)

## Что сделано

- Приложение в `myapp/app.py`, тесты в `tests/test_app.py`.
- Установка пакета через `pyproject.toml`.
- Workflow `.github/workflows/ci.yml`: Python 3.9–3.12, flake8, pytest.
- Сборка Docker-образа после тестов при push в main.

## Запуск

```bash
pip install -e .
pip install pytest
pytest tests/
docker build -t my-python-app .
docker run --rm my-python-app
```

Материалы перенесены без скриншотов. Запуски CI в новом репозитории требуют отдельной проверки.

## Результат

- [GitHub Actions](https://github.com/f1ble/my-python-app/actions)
