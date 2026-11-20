# Использовать каталог в notebook

Выберите ядро Python из проектной `.venv`.
Запустите [MLflow](../mlflow/server.md): при создании контекста плагин
может обращаться к серверу, даже если сам пайплайн пока не выполняется.

В начале notebook загрузите расширение Kedro:

```python
%load_ext kedro.ipython
```

Расширение предоставляет `catalog`, `context`, `session` и `pipelines`:

```python
df = catalog.load("source@raw")
df.head()
```

Каталог использует те же профили и пути, что и CLI.
Для смены датасета или перечитывания YAML выполните `%reload_kedro`.

## Перечитывать изменённые Python-функции

```python
%load_ext autoreload
%autoreload 2
```

Autoreload полезен при редактировании импортированных функций без
перезапуска ядра. Он не заменяет перечитывание конфигурации Kedro.
Это удобство для разработки, а не обязательное условие каждого notebook.

## Resolver oc.env

При загрузке через Kedro используется проектный `settings.py`:
он загружает `.env` и регистрирует resolver `oc.env`. 


Использование функций из `project/` не влечет за собой запуск kedro или mlflow серверов, но до тех пор, пока в самих функциях не используются инструменты
Для ручной записи результатов см. [MLflow в notebook](../mlflow/notebook.md).

[Kedro в Jupyter](https://docs.kedro.org/en/stable/integrations-and-plugins/notebooks_and_ipython/kedro_and_notebooks/)

[Вопросы раздела](../README.md#kedro) · [Все инструкции](../README.md)
