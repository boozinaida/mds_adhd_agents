# mds_adhd_agents
# LangGraph Planner Agent with Ollama

POC-проект для создания локального AI-агента на базе **LangGraph**, **Ollama** и **Jupyter Notebook**.

## Что делает проект

Проект поднимает локальную среду, в которой можно:
- запускать модель `gemma3:1b` через Ollama,
- разрабатывать и тестировать агента в Jupyter Notebook,
- строить planner-agent на LangGraph,
- разбивать задачи на подзадачи и формировать план дня.

## Стек

- Docker Compose
- Ollama
- Jupyter Notebook / JupyterLab
- LangGraph
- LangChain
- langchain-ollama
- Pydantic


## Старт

### 0. Запустить Docker Desktop
Проверить, что Engine running и что включён режим Linux containers.

### 1. Клонировать репозиторий

```bash
git clone https://github.com/boozinaida/mds_adhd_agents.git
cd mds_adhd_agents
```

### 2. Запустить окружение

```bash
docker compose up
```

Если в системе используется старая команда Compose:

```bash
docker-compose up
```

### 3. Открыть Jupyter

Открой в браузере:

```text
http://localhost:8888
```

Токен для входа:

```text
langgraph
```

## Сервисы

### Ollama
- URL внутри Docker-сети: `http://ollama:11434`
- URL с хоста: `http://localhost:11434`

### Jupyter
- URL: `http://localhost:8888`

## Ноутбуки

Все ноутбуки хранятся в папке `./notebooks`.

Эта папка примонтирована в контейнер Jupyter, поэтому:
- изменения сохраняются на хостовой машине,
- ноутбуки не теряются после перезапуска контейнеров,
- файлы можно коммитить в Git и совместно редактировать.

## Первый запуск модели

При старте Compose проект должен автоматически скачать модель `gemma3:1b`.

Если модель не загрузилась автоматически, её можно подтянуть вручную:

```bash
docker compose exec ollama ollama pull gemma3:1b
```

Проверить список моделей:

```bash
docker compose exec ollama ollama list
```

## Как работать в проекте

1. Открой notebook `notebooks/01_langgraph_gemma3_1b.ipynb`.
2. Запусти ячейки по порядку.
3. Меняй prompt, graph и логику агента.
4. Сохраняй изменения прямо в `notebooks/`.
5. Делай commit и push в GitHub.

## Полезные команды

### Остановить контейнеры

```bash
docker compose down
```

### Остановить и удалить volume с моделями

```bash
docker compose down -v
```

### Посмотреть логи Jupyter

```bash
docker compose logs -f jupyter
```

### Посмотреть логи Ollama

```bash
docker compose logs -f ollama
```

## Совместная 
