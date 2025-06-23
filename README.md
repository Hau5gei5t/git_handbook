# Справочник по Git для начинающих

## 0. Авторизация через ssh ключ

Генерация пары ключей и вывод публичного ключа
```bash
ssh-keygen -q -t ed25519 -N '' -f .ssh/github_key
cat .ssh/github_key.pub
```

В настройках профиля добавляем публичный ключ:

![изображение](https://github.com/user-attachments/assets/d3307cda-7c57-46d0-bf76-aa23f28f48f9)



## 1. Инициализация репозитория

```bash
git init
```

**Пример:**
```mermaid
gitGraph
  commit id: "Initial commit"
```

## 2. Добавление файлов в staging area

```bash
git add index.html
git commit -m "Initial commit"
```

**Визуализация изменений:**
```mermaid
gitGraph
	commit id: "Initial commit"
	commit id: "Добавлен header"
	commit id: "Исправлена верстка"
```

## 4. Создание веток

```bash
git branch feature/login
git checkout feature/login
```


**Ветвление:**
```mermaid
gitGraph
  commit
  branch feature/login
  checkout feature/login
  commit
  checkout main
  commit
```

## 5. Слияние веток

```bash
git merge feature/login
```

**Пример слияния:**
```mermaid
gitGraph
  commit
  branch feature/login
  checkout feature/login
  commit
  checkout main
  commit
  merge feature/login id: "merge feature" type: NORMAL
```

## 6. Работа с тегами

```bash
git tag v1.0.0
```

**Тегирование:**
```mermaid
gitGraph
  commit tag: "v1.0.0"
  commit
  commit tag: "v1.1.0" type: HIGHLIGHT
```

## 7. Отмена изменений

```bash
git revert <commit-hash>
```
**Пример отката:**
```mermaid
gitGraph
  commit
  commit id: "Ошибочный коммит" type: REVERSE
  commit id: "Откат изменений"
```

## 8. Работа с удалённым репозиторием

Отправить изменения в удаленный репозиторий
```bash
git remote add origin https://github.com/user/repo.git
git push -u origin main
```

**Синхронизация:**

```mermaid
gitGraph
  commit id: "Локальные изменения"
  commit id: "Пуш в origin/main"
```

Получить изменения из удаленного репозитория
```bash
git pull
```

Клонировать репозиторий
```bash
git clone https://github.com/user/repo.git
```

## 9. Пул реквесты (Pull Requests)
Это механизм для уведомления о изменениях в ветке репозитория и их согласования с командой. Используется на платформах GitHub, GitLab и Bitbucket.

**Создание пул реквеста на GitHub:**

1. Отправьте ветку на сервер:
```bash
git push origin feature-branch
```
    
- Перейдите на страницу репозитория → вкладка “Pull Requests” → “New Pull Request”.

![изображение](https://github.com/user-attachments/assets/31692319-cc35-4d2b-9db5-e75b0b12ef2e)

    
- Выберите базовые и сравниваемые ветки, добавьте заголовок и описание.
