# Общие настройки:
1) js.configs.recommended
Рекомендуемые настройки для JavaScript от ESLint.
2) js.configs.recommended
Рекомендуемые настройки для JavaScript от ESLint.
3) plugin:react-hooks/recommended
Рекомендуемые правила для работы с React-хуками.
4) plugin:@typescript-eslint/recommended
Рекомендуемые правила для работы с TypeScript.

# Настройки для файлов:
1) Применяются к файлам с расширениями *.js, *.jsx, *.ts, *.tsx.
2) Используется парсер @typescript-eslint/parser.
ecmaVersion: 2021
3) Поддержка синтаксиса ECMAScript 2021.
sourceType: 'module'

# Поддержка модулей ES.
# Плагины:
1) @typescript-eslint
Для работы с TypeScript.
2) eslint-plugin-import
Управление импортами.
3) eslint-plugin-react-hooks
Правила для хуков React.

# Правила:
# React-хуки:
1) react-hooks/exhaustive-deps: warn
Предупреждать, если зависимости хуков указаны неверно.
2) react-hooks/rules-of-hooks: error
Ошибка, если хуки используются вне функций или не по правилам.

# TypeScript:
1) @typescript-eslint/explicit-module-boundary-types: off
Отключить требование указывать типы для входных данных и результатов функций.
2) @typescript-eslint/no-explicit-any: off
Разрешить использование типа any.
3) @typescript-eslint/no-unused-vars: warn
Предупреждать о неиспользуемых переменных. Игнорировать переменные, начинающиеся с _.

# Общие правила:
1) no-console: warn
Предупреждать при использовании console.
2) prefer-const: warn
Рекомендовать использовать const, если переменная не изменяется.
3) quotes: warn, 'single'
Предупреждать, если строки не в одинарных кавычках.
4) indent: warn, 2
Использовать отступ в 2 пробела.
5) max-len: warn, { code: 120 }
Предупреждать, если длина строки превышает 120 символов.
6) comma-dangle: warn, 'always-multiline'
Требовать запятую в конце многострочных конструкций.
7) semi: warn, 'always'
Требовать точку с запятой в конце выражений.

# Импорты:
1) import/order

# Настроить порядок импортов:
1) builtin – встроенные модули (например, fs, path).
2) external – внешние библиотеки.
3) internal – внутренние модули проекта.
4) parent – модули из родительских директорий.
5) sibling – модули из соседних директорий.
6) index – импорт из index.js.
7) object – импорты объектов.
8) type – импорты типов.
9) newlines-between: always-and-inside-groups
Требовать пустые строки между группами импортов.

# Настройки React:
1) react.version: 'detect'
Автоматически определять версию React для применения правил.

## index.js:
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
