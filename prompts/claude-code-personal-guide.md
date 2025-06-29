# Claude Code: Персональное руководство по настройке и промпт инжинирингу

## 🚀 Быстрый старт

### 1. Установка (за 2 минуты)
```bash
# Установка Node.js 20+ (если еще нет)
curl -fsSL https://deb.nodesource.com/setup_20.x | sudo -E bash -
sudo apt install -y nodejs

# Настройка npm (ВАЖНО: без sudo!)
mkdir -p ~/.npm-global
npm config set prefix ~/.npm-global
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.bashrc
source ~/.bashrc

# Установка Claude Code
npm install -g @anthropic-ai/claude-code

# Первый запуск
claude
```

### 2. Первые команды для проверки
```bash
# В папке проекта
> Explain this codebase structure
> Find all TODO comments
> What are the main dependencies?
> /help
```

---

## ⚙️ Персональная конфигурация

### Базовая настройка (~/.claude/settings.json)
```json
{
  "model": "claude-sonnet-4-20250514",
  "autoAccept": false,
  "maxTokens": 4096,
  "temperature": 0.1,
  "permissions": {
    "allow": [
      // Файловые операции
      "Read(**)",
      "Edit(src/**)",
      "Edit(*.md)",
      "Edit(*.json)",
      "Edit(*.yaml)",
      "Edit(*.yml)",
      
      // Git команды
      "Bash(git status)",
      "Bash(git diff *)",
      "Bash(git log *)",
      "Bash(git add *)",
      "Bash(git commit *)",
      "Bash(git push)",
      "Bash(git pull)",
      
      // Инструменты разработки
      "Bash(npm run *)",
      "Bash(yarn *)",
      "Bash(pnpm *)",
      "Bash(docker compose *)",
      "Bash(python *)",
      "Bash(pip install *)",
      
      // Полезные команды
      "Bash(ls *)",
      "Bash(cat *)",
      "Bash(grep *)",
      "Bash(find *)",
      
      // Web запросы (документация)
      "WebFetch(domain:docs.anthropic.com)",
      "WebFetch(domain:developer.mozilla.org)",
      "WebFetch(domain:stackoverflow.com)",
      "WebFetch(domain:github.com)"
    ],
    "deny": [
      // Защита от опасных операций
      "Edit(.env*)",
      "Edit(~/.ssh/**)",
      "Edit(/etc/**)",
      "Bash(rm -rf *)",
      "Bash(sudo *)",
      "Bash(chmod 777 *)",
      "Bash(npm publish)",
      "Read(/var/log/secure)"
    ]
  },
  "mcpServers": {
    "filesystem": {
      "type": "stdio",
      "command": "npx",
      "args": ["-y", "@modelcontextprotocol/server-filesystem", "~/Documents", "~/Projects"]
    }
  }
}
```

### Настройки для конкретного проекта (.claude/settings.json)
```json
{
  "permissions": {
    "allow": [
      "Bash(npm test)",
      "Bash(npm run build)",
      "Bash(npm run lint)",
      "Edit(src/**)",
      "Edit(tests/**)",
      "Read(docs/**)"
    ]
  }
}
```

### Локальные настройки (.claude/settings.local.json)
```json
{
  "model": "claude-opus-4-20250514",  // Для сложных задач
  "permissions": {
    "allow": [
      "Bash(./local-dev.sh)",
      "Edit(//tmp/cache/**)"
    ]
  }
}
```

---

## 🧠 Настройка памяти Claude

### Глобальная память (~/.claude/CLAUDE.md)
```markdown
# Мои персональные предпочтения

## Стиль кодирования
- TypeScript везде, где возможно
- Отступы: 2 пробела
- Точка с запятой: всегда
- Кавычки: одинарные для строк
- Максимум 100 символов в строке

## Предпочтения в коде
- Функциональный подход предпочтительнее ООП
- Использовать async/await вместо промисов
- Деструктуризация для извлечения свойств
- Ранний return для проверок

## Git
- Conventional commits (feat:, fix:, docs:, etc.)
- Ветки: feature/*, bugfix/*, hotfix/*
- Squash коммиты перед merge

## Тестирование
- Jest для unit тестов
- Playwright для e2e
- Минимум 80% покрытия
- Тестировать edge cases

## Документация
- JSDoc для публичных API
- README с примерами использования
- Комментарии только для сложной логики
```

### Проектная память (./CLAUDE.md)
```markdown
# Проект: [Название проекта]

## Архитектура
- Frontend: React + TypeScript + Vite
- Backend: Node.js + Express + PostgreSQL
- Стейт: Redux Toolkit
- Стили: Tailwind CSS

## Структура проекта
```
src/
├── components/     # Переиспользуемые компоненты
├── features/       # Фичи по доменам
├── hooks/          # Кастомные хуки
├── services/       # API и внешние сервисы
├── store/          # Redux store
├── types/          # TypeScript типы
└── utils/          # Вспомогательные функции
```

## API endpoints
- `/api/auth/*` - аутентификация
- `/api/users/*` - управление пользователями
- `/api/projects/*` - проекты

## Переменные окружения
- `DATABASE_URL` - строка подключения к БД
- `JWT_SECRET` - секрет для токенов
- `API_PORT` - порт сервера (default: 3000)

## Команды разработки
- `npm run dev` - запуск в dev режиме
- `npm run test:watch` - тесты с hot reload
- `npm run db:migrate` - миграции БД
```

### Локальная память проекта (./CLAUDE.local.md)
```markdown
# Локальные настройки

## Тестовые данные
- Тестовый юзер: test@example.com / password123
- Локальная БД: postgresql://localhost:5432/myapp_dev

## Мои текущие задачи
- [ ] Рефакторинг компонента UserProfile
- [ ] Добавить валидацию в форму регистрации
- [ ] Исправить баг с кешированием

## Заметки
- Баг в продакшене: проблема с CORS на /api/upload
- Оптимизировать запрос getUserProjects() - слишком медленный
```

---

## 🎯 Промпт инжиниринг для Claude Code

### Эффективные промпты для разных задач

#### 1. Понимание кода
```bash
# Обзор архитектуры
> Provide a comprehensive overview of this codebase architecture, focusing on:
  1. Main components and their interactions
  2. Data flow between modules
  3. Key design patterns used
  4. Potential bottlenecks or issues

# Анализ зависимостей
> Analyze the dependency structure and identify:
  - Core dependencies vs dev dependencies
  - Outdated packages that need updates
  - Potential security vulnerabilities
  - Unnecessary dependencies we can remove
```

#### 2. Рефакторинг
```bash
# Модернизация кода
> Refactor this [component/module] to:
  - Use modern React patterns (hooks, functional components)
  - Improve performance with memoization where needed
  - Add proper TypeScript types
  - Follow our coding standards from CLAUDE.md
  Show me the changes step by step before applying

# Оптимизация производительности
> think deeply about performance bottlenecks in this module and suggest optimizations for:
  - Reducing re-renders
  - Optimizing database queries
  - Implementing proper caching
  - Reducing bundle size
```

#### 3. Отладка и исправление багов
```bash
# Диагностика ошибки
> I'm getting this error: [ERROR]. Help me:
  1. Identify the root cause
  2. Trace through the execution flow
  3. Find all related code that might be affected
  4. Propose a fix with tests

# Комплексная отладка
> ultrathink about why this feature works in development but fails in production. Consider:
  - Environment differences
  - Build process issues
  - Race conditions
  - Memory/resource constraints
```

#### 4. Создание новых функций
```bash
# Пошаговая реализация
> Let's implement [feature] using TDD approach:
  1. First, write comprehensive tests for expected behavior
  2. Create the minimal implementation to pass tests
  3. Refactor for code quality
  4. Add edge case handling
  5. Update documentation

# Архитектурное планирование
> think harder about the best architecture for implementing [feature] considering:
  - Scalability for 100K+ users
  - Maintainability over 3+ years
  - Integration with existing systems
  - Performance requirements
  - Security implications
```

#### 5. Работа с тестами
```bash
# Создание тестов
> Create comprehensive tests for [module] that:
  - Cover all public methods
  - Test edge cases and error conditions
  - Include integration tests
  - Add performance benchmarks
  - Use realistic test data

# Улучшение покрытия
> Analyze test coverage and:
  1. Identify untested code paths
  2. Add tests for critical business logic
  3. Create tests for error scenarios
  4. Add snapshot tests for UI components
```

### Extended Thinking стратегии

#### Когда использовать разные уровни
- **`think`** (4K токенов) - простой анализ, планирование рефакторинга
- **`think deeply`** (10K токенов) - архитектурные решения, сложные баги
- **`ultrathink`** (32K токенов) - масштабные изменения, критические проблемы

#### Примеры эффективного использования
```bash
# Архитектурное решение
> think harder about migrating from REST to GraphQL:
  - Analyze current API usage patterns
  - Design the GraphQL schema
  - Plan incremental migration strategy
  - Consider performance implications
  - Estimate implementation timeline

# Сложная отладка
> ultrathink about this memory leak in production:
  - Analyze heap snapshots patterns
  - Trace object retention paths
  - Identify circular references
  - Review event listener cleanup
  - Propose monitoring strategy

# Оптимизация производительности
> think deeply about optimizing this React app that's slow with 10K items:
  - Profile rendering bottlenecks
  - Implement virtualization strategy
  - Optimize state management
  - Review component architecture
  - Add performance monitoring
```

---

## 📌 Полезные Slash-команды

### Создание собственных команд

#### Команды проекта (.claude/commands/)

**review.md** - Код ревью
```markdown
Perform a thorough code review of the changes focusing on:
1. Code quality and readability
2. Potential bugs or edge cases
3. Performance implications
4. Security vulnerabilities
5. Adherence to our coding standards in CLAUDE.md
6. Test coverage adequacy

Provide specific, actionable feedback with code examples.
```

**optimize.md** - Оптимизация
```markdown
Analyze this code for performance optimization opportunities:
1. Identify computational bottlenecks
2. Find unnecessary re-renders or recalculations
3. Suggest caching strategies
4. Recommend algorithmic improvements
5. Propose database query optimizations

Prioritize optimizations by impact and implementation effort.
```

**test.md** - Генерация тестов
```markdown
Create comprehensive tests including:
1. Unit tests for all public methods
2. Integration tests for API endpoints
3. Edge cases and error scenarios
4. Performance benchmarks where relevant
5. Mock external dependencies appropriately

Follow our testing conventions from CLAUDE.md.
```

**security.md** - Аудит безопасности
```markdown
Conduct a security audit examining:
1. Input validation and sanitization
2. Authentication and authorization
3. SQL injection vulnerabilities
4. XSS prevention
5. Sensitive data exposure
6. CSRF protection
7. Rate limiting needs

Provide severity ratings and remediation steps.
```

#### Личные команды (~/.claude/commands/)

**explain.md** - Объяснение кода
```markdown
Explain this code in detail:
1. What problem it solves
2. How it works step-by-step
3. Key algorithms or patterns used
4. Potential improvements
5. Common pitfalls to avoid

Use simple language and provide examples.
```

**refactor-functional.md** - Функциональный рефакторинг
```markdown
Refactor this code to functional style:
- Replace classes with functions
- Use pure functions where possible
- Implement immutability
- Apply functional composition
- Add proper TypeScript types
- Maintain the same public API
```

---

## 🔄 Рабочие процессы

### Ежедневная разработка
```bash
# Начало дня
> What are the high-priority TODOs in this codebase?
> Are there any failing tests or linting errors?
> Show me recent changes that might affect my current task

# Перед коммитом
> /project:review  # Ревью изменений
> Run all tests and fix any failures
> claude commit     # Создание коммита

# Конец дня
> Summarize what we accomplished today
> # Update TODO list with tomorrow's priorities
```

### Работа с legacy кодом
```bash
# Шаг 1: Понимание
> Map out the dependencies and interactions in this legacy module

# Шаг 2: Тесты
> Create tests for the current behavior before refactoring

# Шаг 3: Постепенный рефакторинг
> Refactor this module incrementally:
  1. Extract pure functions
  2. Add TypeScript types
  3. Modernize syntax
  4. Improve error handling
  Keep functionality identical

# Шаг 4: Документация
> Document the refactored code and update README
```

### Исправление сложных багов
```bash
# Воспроизведение
> Help me create a minimal reproduction of this bug

# Анализ
> think deeply about possible root causes considering:
  - Recent code changes
  - Environment differences
  - Race conditions
  - Edge cases

# Исправление
> Implement a fix with:
  1. Root cause addressing
  2. Regression tests
  3. Error handling improvements
  4. Logging for future debugging

# Верификация
> Verify the fix doesn't break existing functionality
```

---

## 🛡️ Безопасность и best practices

### Безопасная конфигурация
```json
{
  "permissions": {
    "allow": [
      // Только необходимые разрешения
      "Read(src/**)",
      "Edit(src/**)",
      "Bash(npm test)"
    ],
    "deny": [
      // Блокировка критических операций
      "Edit(.env*)",
      "Edit(*.key)",
      "Edit(*.pem)",
      "Bash(curl *)",
      "Bash(wget *)",
      "WebFetch"  // Если не нужен внешний доступ
    ]
  }
}
```

### Проверка безопасности
```bash
# Регулярный аудит
> Review our current permission settings for security risks
> Check for any sensitive data in the codebase
> Identify potential security vulnerabilities in dependencies

# Перед деплоем
> Scan for hardcoded secrets or API keys
> Review all environment variable usage
> Check for proper input validation
```

---

## 💡 Продвинутые техники

### Цепочки промптов для сложных задач
```bash
# Промпт 1: Анализ
> Analyze the current authentication system and identify all components involved

# Промпт 2: Планирование
> Based on the analysis, create a plan to migrate from JWT to session-based auth

# Промпт 3: Реализация
> Implement the migration plan step by step with tests

# Промпт 4: Верификация
> Review the implementation for security issues and edge cases
```

### Работа с большими кодовыми базами
```bash
# Используйте XML теги для структурирования
> <context>
  We're working on a large e-commerce platform with 500K+ LOC
  Main issues: slow checkout, complex state management
  </context>
  
  <task>
  Create a plan to refactor the checkout flow for better performance
  </task>

# Фокусируйтесь на конкретных модулях
> Focus only on the payments module and its direct dependencies
```

### Автоматизация с Claude
```bash
# Создание скрипта для регулярных задач
cat > check-quality.sh << 'EOF'
#!/bin/bash
claude --print "Run linting and show only errors" 
claude --print "Check for unused dependencies"
claude --print "Find TODO comments older than 30 days"
EOF

chmod +x check-quality.sh
```

---

## 🚨 Устранение проблем

### Частые проблемы и решения

```bash
# Медленные ответы
> /model claude-sonnet-4  # Переключение на более быструю модель

# Превышение контекста
> Focus only on the UserService class, not the entire module

# Неточные изменения
> Show me the exact changes before applying them
> Apply changes one file at a time

# Проблемы с разрешениями
> /allowed-tools  # Проверка текущих разрешений
```

### Отладка конфигурации
```bash
# Проверка настроек
cat ~/.claude/settings.json | jq .
cat .claude/settings.json | jq .

# Просмотр активных разрешений
> /allowed-tools

# Сброс настроек
mv ~/.claude/settings.json ~/.claude/settings.json.backup
claude  # Перезапуск с дефолтными настройками
```

---

## 📚 Дополнительные ресурсы

### Полезные MCP серверы
```bash
# Sequential thinking для сложных задач
claude mcp add sequential-thinking -s user -- npx -y @modelcontextprotocol/server-sequential-thinking

# Puppeteer для веб-автоматизации
claude mcp add puppeteer -s user -- npx -y @modelcontextprotocol/server-puppeteer
```

### Интеграция с IDE
- VS Code: установите официальное расширение
- Vim: добавьте `command! Claude !claude` в .vimrc
- JetBrains: используйте встроенный терминал

### Где получить помощь
- `/bug` - отправка багрепортов
- [Discord сообщество](https://discord.gg/anthropic)
- [GitHub issues](https://github.com/anthropics/claude-code)
- [Официальная документация](https://docs.anthropic.com/en/docs/claude-code/)

---

## 🎓 Финальные советы

1. **Начните с простого** - не перегружайте Claude сложными инструкциями сразу
2. **Используйте память** - настройте CLAUDE.md для каждого проекта
3. **Экспериментируйте с thinking** - найдите оптимальный уровень для ваших задач
4. **Создавайте команды** - автоматизируйте повторяющиеся задачи
5. **Следите за безопасностью** - регулярно проверяйте разрешения
6. **Итерируйте промпты** - улучшайте формулировки based on результатах

> 💡 **Помните**: Claude Code - это ваш AI напарник. Общайтесь с ним как с опытным коллегой, объясняйте контекст и будьте конкретны в запросах!
