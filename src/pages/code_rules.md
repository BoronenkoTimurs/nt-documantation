# Правила написания кода

## Общие правила

1. **Кавычки**:
   - Используйте двойные кавычки (`""`) только для `className`.
   - В остальных случаях используйте одинарные кавычки (`''`).
   - Статьи:
     - [JS quote best practices? ES6 / React -- single, double, backticks?](https://stackoverflow.com/questions/44208081/js-quote-best-practices-es6-react-single-double-backticks)

2. **Импорты**:
   - Разделяйте `import` из библиотек и `import` из модулей пробелом.
   - Сначала должны идти `import <name>`, затем `import { <name> }`.
   - Пример:
     ```javascript
     import React from 'react';
     import { useState } from 'react';

     import Icon from '@/components/custom/icon';
     import { cn } from "@/lib/utils"
     ```
    - Подробнее про использование динамических improt смотреть в разделе "Дополнительные рекомендации" пункт первый.
3. **Закрывающиеся тэги**:
   - Закрывающиеся тэги должны быть без пробела в конце.
   - <span style={{color: "green"}}>Правильно:</span> `<MyComponent/>`
   - <span style={{color: "red"}}>Неправильно</span>: `<MyComponent />`

4. **Точки с запятой**:
   - Расставляйте точки с запятой в конце переменных(`const`, `let`), `import`, `export`.
   - Пример:
      ```javascript
      import { useForm } from 'react-hook-form';

      const formSchema = z.object({
        example1: z.string().min(1),
        example2: z.string().min(1),
      });

      type ExampleFormValue = z.infer<typeof formSchema>;

      export default ExampleForm;
      ```
    - <span style={{color: "green"}}>Исключение</span> - в `interface` нужно ставить `,`.
    - Пример:
        ```javascript
        interface ExampleProps {
          example1: string,
          example2: string,
          example3: boolean,
        };
        ```

5. **Форматирование атрибутов**:
   - Если компонент имеет 3 и больше атрибутов, они должны быть написаны в столбик.
   - Пример:
     ```javascript
     <Button
       disabled={loading}
       variant='destructive'
       size='sm'
       onClick={() => setOpen(true)}
     >
       <Icon name='trash'/>
     </Button>
     ```

6. **Форматирование `import`**:
   - Если `import` содержит 3 и больше модулей, они должны быть написаны в столбик.
   - Пример:
     ```javascript
     import {
       useState,
       useEffect,
       useRef
     } from 'react';
     ```

7. **Разделение логики**:
   - Разделяйте и группируйте части кода, которые отвечают за разную логику, пробелами.
   - Пример:
     ```javascript
     const handleClick = () => {
       // handle click logic
     };

     const handleChange = () => {
       // handle change logic
     };

     return (
       <div>
         <Button onClick={handleClick}>Click me</Button>
         <Input onChange={handleChange}/>
       </div>
     );
     ```

## Дополнительные рекомендации

1. **Динамические импорты и разделение кода**:
   - Используйте динамические импорты и разделение кода для улучшения производительности.
   - Статьи:
     - [React Dynamic Imports & Route-centric Code Splitting Guide](https://blog.logrocket.com/react-dynamic-imports-route-centric-code-splitting-guide/)
     - [Code Splitting](https://legacy.reactjs.org/docs/code-splitting.html)

2. **Понятность и самодокументирование**:
   - Пишите код так, чтобы он был самодокументирующим. Имя переменной, функции или компонента должно описывать его назначение.
   - Пример:
     ```javascript
     const fetchData = async () => {
       // fetch data logic
     };

     const handleFormSubmit = (event) => {
       event.preventDefault();
       // handle form submit logic
     };
     ```

3. **Использование комментариев**:
   - Используйте комментарии для объяснения сложной логики или важных деталей кода.
   - Пример:
     ```javascript
     // This function handles the API call to fetch user data
     const fetchUserData = async (userId) => {
       // fetch user data logic
     };
     ```
4. **Использование alias в import**:
   - Используйте alias для сокращения длинных путей и улучшения читаемости кода.
   - Настройки alias в файле конфигурации - `tsconfig.json`.
   - Пример настроенного alias в `tsconfig.json`:
      ```json
      {
        "compilerOptions": {
          "baseUrl": ".",
          "paths": {
            "@/*": ["./src/*"]
          }
        }
      }
      ```
   - Пример использования alias в коде:
     ```javascript
     import useDelete from '@/hooks/useDelete';
     import { Button } from '@/components/ui/button';
     ```