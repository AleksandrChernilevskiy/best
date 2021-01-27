## **1. Используй === вместо ==**

> Всегда используй ===/!== вместо ==/!=, предотвращает ошибки приведения типов
>> eslint: [eqeqeq](https://eslint.org/docs/rules/eqeqeq#top)


:x: не надо так :point_down:
```
a == b 
foo == true
bananas != 1
value == undefined
```

:white_check_mark: надо так :point_down:
```
typeof foo === 'undefined'
'hello' !== 'world'
0 === 0
true === true
foo === null
```

Существуют Исключения
+ Сравнение двух литеральных значений
+ сравнение с null
+ вызов typrof



## **2. Никогда не используй функцию eval()**

> С помощью данной функции мы можем выполнить код переданой ей в строке.
> При её использовании:
>> + Снижаеться производительность
>> + Возникает огромный риск, связанный с нарушением секретности
>> + Переданной строке передаются значительные полномочия
>>> eslint: [no-eval](https://eslint.org/docs/rules/no-eval#top)

:x: не надо так :point_down:
```
let obj = { x: "foo" },
  key = "x",
  value = eval("obj." + key);
```

:white_check_mark: надо так :point_down:
```
let obj = { x: "foo" },
  key = "x",
  value = obj[key];
```



## **3. Размещайте ваш скрипт в конце страницы**

> Главная цель загрузить страницу максимально быстро, выполнение скрипта может задержать загрузку страницы и пользователю придётся ждать пока что то появиться.
>>eslint: [body_style](https)

:x: не надо так :point_down:
```
<html>
  <head>
    <script type="text/javascript" src="path/to/file.js"></script>
    <script type="text/javascript" src="path/to/anotherFile.js"></script>
  </head>
  <body>
  </body>
</html>
```

:white_check_mark: надо так :point_down:
```
<p>And now you know my favorite kinds of corn. </p>
 <script type="text/javascript" src="path/to/file.js"></script>
 <script type="text/javascript" src="path/to/anotherFile.js"></script>
 </body>
 </html>
```


## **4. Уменьшаем количество переменных в глобальной области видимости**

> Снижается вероятность взаимодействия с данной переменной других библиотек, виджетов, приложений.

:x: не желательно :point_down:
```
var name = 'Jeffrey';
 var lastName = 'Way';
  
 function doSomething() {...}
  
 console.log(name); // Jeffrey -- or window.name
```

:white_check_mark: надо так :point_down:
```
var DudeNameSpace = {
    name : 'Jeffrey',
    lastName : 'Way',
    doSomething : function() {...}
 }
 console.log(DudeNameSpace.name); // Jeffrey
```
След вывода меньше.



## **5. Комментируй код**

> Так код будет понятнее для твоих коллег и для тебя если ты вернёшься к коду через продожительное время.

:white_check_mark: надо так :point_down:
```
// Тут будет мой комментарий. 
 for(var i = 0, len = array.length; i < len; i++) {
    console.log(array[i]);
 }
```

*В комментариях после // или /* должен быть пробел.*
>eslint: [spaced-comment](https://github.com/WebHeroSchool/JavaScript_Style_Guide/blob/master)

:x: не надо так :point_down:
```
/is current tab
const active = true;

/**
 *make() returns a new element
 *based on the passed-in tag name
 */
function make(tag) {

  // ...

  return element;
}
```

:white_check_mark: надо так :point_down:
```
// is current tab
const active = true;


/**
 * make() returns a new element
 * based on the passed-in tag name
 */
function make(tag) {

  // ...

  return element;
}
```



## **6. Не передавайте строку в "SetInterval" или "SetTimeOut"**

> При передаче строки в "SetInterval" или "SetTimeOut" получаеться точно такая же ситуация как с функцией eval()

:x: не надо так :point_down:
```
setInterval(
 "document.getElementById('container').innerHTML += 'My new number: ' + i", 3000
 );
```

:white_check_mark: надо так :point_down:
```
setInterval(someFunction, 3000);
```


## **7. Используйте {} вместо New Object()**

> Интуитивно понятнее и приятнее. new object() зарекомендовал себя как плохая практика.
>> eslint: [no-new-object](https://eslint.org/docs/rules/no-new-object#top)

:x: не надо так :point_down:
```
const item = new Object();
```

:white_check_mark: надо так :point_down:
```
const item = {};
```


## **8. Используйте [] вместо New Array()**

> Такая же ситуация как и с new object().
>> eslint: [no-array-constructor](https://eslint.org/docs/rules/no-array-constructor#top)

:x: не надо так :point_down:
```
const items = new Array();
```

:white_check_mark: надо так :point_down:
```
const items = [];
```


## **9. Всегда, всегда используйте точки с запятой (;)**

> Могут возникнуть очень сложные вариации использования функций, приложений и т.д. Поставив ; мы обезопасим переменную и другие составляющие.

:x: не надо так :point_down:
```
var someItem = 'some string'
 function doSomething() {
   return 'something'
 }
```

:white_check_mark: надо так :point_down:
```
var someItem = 'some string';
 function doSomething() {
   return 'something';
 }
```


## **10. Не делайте слишком много вложений**

> Слишкой большое вложение сделай код нечитабельным.

:x: не надо так :point_down:
```
firstFunction ( args , function () { 
    secondFunction ( args , function () { 
        thirdFunction ( args , function () { 
            // И так далее…
         }); 
    }); 
});
```