# 01. Первый Pipeline на CI в GitHub Actions

Простейший workflow GitHub Actions: выводит приветствие при каждом push.

## Задание

Источник: [content/DevOps/CI_CD/Pipelines/hello.md](https://gitflic.ru/project/rurewa/mfua/blob?file=content/DevOps/CI_CD/Pipelines/hello.md&branch=master)
Репозиторий: [f1ble/my-first-cicd](https://github.com/f1ble/my-first-cicd)

## Что сделано

- Создан публичный репозиторий `my-first-cicd` на GitHub
- Исходный проект перенесён в отдельный репозиторий
- Создана структура `.github/workflows/hello.yml`
- Workflow запускается при каждом push

## Структура проекта

```
my-first-cicd/
├── .github/
│   └── workflows/
│       └── hello.yml
└── README.md
```

## Содержимое `.github/workflows/hello.yml`

```yaml
name: Мой первый workflow
on: [push]
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Запустить команду
        run: echo "Привет, мир! Я только что запустил CI!"
```

## Команды

```bash
git clone https://github.com/f1ble/my-first-cicd.git
cd my-first-cicd
mkdir -p .github/workflows
touch .github/workflows/hello.yml
git add .
git commit -m "Add first workflow"
git push origin main
```

## Результат

- [GitHub Actions](https://github.com/f1ble/my-first-cicd/actions)

- Код и workflow перенесены; результат запуска CI см. в Actions.
