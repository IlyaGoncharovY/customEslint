# Custom ESLint Configuration
## Кастомная конфигурация ESLint для проектов на React и TypeScript.
Этот пакет предоставляет готовую конфигурацию ESLint для работы с JavaScript, TypeScript, React и хуками React. Он обеспечивает единообразие в коде и помогает избегать распространенных ошибок.

## Особенности
1) Рекомендуемые конфигурации:
 - JavaScript `(js.configs.recommended)`
 - React-хуки `(plugin:react-hooks/recommended)`
 - TypeScript `(plugin:@typescript-eslint/recommended)`
2) Поддержка ECMAScript 2021 и модулей ES.
3) Интеграция с плагинами:
 - TypeScript `(@typescript-eslint)`
 - Управление импортами `(eslint-plugin-import)`
 - Хуки React `(eslint-plugin-react-hooks)`
4) Комплексные правила для обеспечения единообразного стиля кода.

## Детали конфигурации
### Общие настройки
1) `js.configs.recommended` - 
Рекомендуемые настройки для JavaScript от ESLint.
2) `plugin:react-hooks/recommended` - 
Рекомендуемые правила для работы с хуками React.
3) `plugin:@typescript-eslint/recommended` - 
Рекомендуемые правила для TypeScript.

## Настройки для файлов
1) Применяется к файлам с расширениями: `*.js`, `*.jsx`, `*.ts`, `*.tsx`.
2) Используется парсер: `@typescript-eslint/parser`.
3) `ecmaVersion: 2021` -
Поддержка синтаксиса ECMAScript 2021.
4) `sourceType: 'module'` - 
Поддержка модулей ES.

## Плагины
1) `@typescript-eslint` - 
Для проверки TypeScript.
2) `eslint-plugin-import` - 
Для управления порядком импортов.
3) `eslint-plugin-react-hooks` - 
Для проверки правил использования хуков React.

## Правила
### Хуки React
1) `react-hooks/exhaustive-deps: warn` - 
Предупреждать, если зависимости в хуках указаны неверно.
2) `react-hooks/rules-of-hooks: error` - 
Выдавать ошибку, если хуки используются не по правилам.
### TypeScript
1) `@typescript-eslint/explicit-module-boundary-types: off` - 
Отключить обязательное указание типов для входных и выходных данных функций.
2) `@typescript-eslint/no-explicit-any: off` - 
Разрешить использование типа `any`.
3) `@typescript-eslint/no-unused-vars: warn` - 
Предупреждать о неиспользуемых переменных, игнорируя переменные, начинающиеся с `_`.
### Общие правила
1) `no-console: warn` - 
Предупреждать при использовании `console`.
2) `prefer-const: warn` - 
Рекомендовать использовать `const`, если переменная не изменяется.
3) `quotes: warn, 'single'` - 
Требовать использование одинарных кавычек для строк.
4) `indent: warn, 2` - 
Требовать отступ в 2 пробела.
5) `max-len: warn, { code: 120 }` -
Предупреждать, если длина строки превышает 120 символов.
6) `comma-dangle: warn, 'always-multiline'` - 
Требовать запятые в конце многострочных конструкций.
7) `semi: warn, 'always'` - 
Требовать точки с запятой в конце выражений.
### Импорты
1) `import/order` - 
Настроить порядок импортов:
 - `builtin` – Встроенные модули (например, `fs`, `path`).
 - `external` – Внешние библиотеки.
 - `internal` – Внутренние модули проекта.
 - `parent` – Модули из родительских директорий.
 - `sibling` – Модули из соседних директорий.
 - `index` – Импорты из `index.js`.
 - `object` – Импорты объектов.
 - `type` – Импорты типов.
 - `newlines-between: always-and-inside-groups` -
Требовать пустые строки между группами импортов.

## Настройки React
1) `react.version: 'detect'` - 
Автоматически определять версию React для корректной работы правил.

## Использование
1) ### Установите пакет:

```bash
npm install npm i @ilya_goncharov_y/customeslint --save-dev
```

2) ### Настройте ESLint в проекте: Создайте файл eslint.config.js в корне проекта:

```js
import eslintConfig from '@ilya_goncharov_y/customeslint';

export default eslintConfig;
```

3) ### Запустите ESLint:

```bash
npx eslint .
```

## Пример конфигурации
Вот полная конфигурация, экспортируемая этим пакетом:
```js
export default [
    js.configs.recommended,
    ...compat.extends('plugin:react-hooks/recommended'),
    ...compat.extends('plugin:@typescript-eslint/recommended'),

    {
        files: ['**/*.js', '**/*.jsx', '**/*.ts', '**/*.tsx'],
        languageOptions: {
            parser: parser,
            ecmaVersion: 2021,
            sourceType: 'module',
        },
        plugins: {
            '@typescript-eslint': typescriptEslint,
            import: importPlugin,
            'react-hooks': reactHooks,
        },
        rules: {
            'react-hooks/exhaustive-deps': 'warn',
            'react-hooks/rules-of-hooks': 'error',
            '@typescript-eslint/explicit-module-boundary-types': 'off',
            '@typescript-eslint/no-explicit-any': 'off',
            '@typescript-eslint/no-unused-vars': ['warn', { argsIgnorePattern: '^_' }],
            'no-console': 'warn',
            'prefer-const': 'warn',
            quotes: ['warn', 'single'],
            indent: ['warn', 2],
            'max-len': ['warn', { code: 120 }],
            'comma-dangle': ['warn', 'always-multiline'],
            semi: ['warn', 'always'],
            'import/order': [
                'warn',
                {
                    groups: ['builtin', 'external', 'internal', 'parent', 'sibling', 'index', 'object', 'type'],
                    'newlines-between': 'always-and-inside-groups',
                },
            ],
        },
        settings: {
            react: {
                version: 'detect',
            },
        },
    },
];
```
