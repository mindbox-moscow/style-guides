# Стандарты кодирования — TypeScript

### Форматирование
Для отступов используем табуляцию.
Для фигурных скобок испольузем K&R стиль:
```typescript
interface Foo {
    bar: string;
}
```

##### Длина строки
- Максимальная допустимая длина строки — 130 символов
- Символ табуляция считается за 4 символа
- Пробельные символы в конце строки учитываются

### Именование
- Имя файла соответствует имени класса. В случае с React - имени компонента.
- Компоненты-контейнеры не имеют постфикса.
- Компоненты-рисовашки имеют постфикс Presenter

### Типизация props
```typescript
// Каждый интерфейс -- опционален.
export interface StateProps {}
export interface DispatchProps {}
export interface OwnProps {}

interface Props extends StateProps, DispatchProps, OwnProps  {}
```
Если у _Presenter_ есть `OwnProps`, то они внутри презентера лежат.
Если у _Container_ есть `OwnProps`, то они лежат внутри контейнера.

### Деление React-компонентов на файлы
##### Минимальный вариант
- MyComponent - контейнер
- MyComponentPresenter - презентер
- MyComponentReducer - Reducer, Actions, Action Creators
##### Средний вариант
- MyComponent - контейнер
- MyComponentPresenter - презентер
- MyComponentReducer - Reducer
- MyComponentActions - Actions, Action Creators
##### Максимальный вариант
- MyComponent - контейнер
- MyComponentPresenter - презентер
- MyComponentReducer - Reducer
- MyComponentActionCreators - Action Creators
- MyComponentActions - Actions

### Папки
Группируем файлы по папкам соответственно функционалу, а не архитектурным срезам. Пример:
```
Operation
    OperationSteps
        AddOrEditOperationStep
            AddOrEditOperationStep.ts
            AddOrEditOperationStepPresenter.tsx
            AddOrEditOperationStepReducer.ts
        SendEmailOperationStep
            <files>
    OutptutWriters
        CustomerOutputWriter
            <files>
 ```
