# Javascript ���� ����
https://github.com/leonardomso/33-js-concepts�� �����Ͽ� �ڹ� ��ũ��Ʈ �����ڰ� �˾ƾ��� ������ �����ߴ�.

---

## ����
1.  **[Call Stack](#call-stack)**
1.  **[Primitive Types](#primitive-types)**
1.  **[Value Types and Reference Types](#value-types-and-reference-types)**
1.  **[Implicit, Explicit, Nominal, Structuring and Duck Typing](#implicit-explicit-nominal-structuring-and-duck-typing)**
1.  **[== vs === vs typeof](#-vs--vs-typeof)**
1.  **[Function Scope, Block Scope and Lexical Scope](#function-scope-block-scope-and-lexical-scope)**
1.  **[Expression vs Statement](#expression-vs-statement)**
1.  **[IIFE, Modules and Namespaces](#iife-modules-and-namespaces)**
1.  **[Message Queue and Event Loop](#message-queue-and-event-loop)**
1.  **[setTimeout, setInterval and requestAnimationFrame](#settimeout-setinterval-and-requestanimationframe)**
1.  **[JavaScript Engines](#javascript-engines)**
1.  **[Bitwise Operators, Type Arrays and Array Buffers](#bitwise-operators-type-arrays-and-array-buffers)**
1.  **[DOM and Layout Trees](#dom-and-layout-trees)**
1.  **[Factories and Classes](#factories-and-classes)**
1.  **[this, call, apply and bind](#this-call-apply-and-bind)**
1.  **[new, Constructor, instanceof and Instances](#new-constructor-instanceof-and-instances)**
1.  **[Prototype Inheritance and Prototype Chain](#prototype-inheritance-and-prototype-chain)**
1.  **[Object.create and Object.assign](#objectcreate-and-objectassign)**
1.  **[map, reduce, filter](#map-reduce-filter)**
1.  **[Pure Functions, Side Effects and State Mutation](#pure-functions-side-effects-and-state-mutation)**
1.  **[Closures](#closures)**
1.  **[High Order Functions](#high-order-functions)**
1.  **[Recursion](#recursion)**
1.  **[Collections and Generators](#collections-and-generators)**
1.  **[Promises](#promises)**
1.  **[async/await](#asyncawait)**
1.  **[Data Structures](#data-structures)**
1.  **[Expensive Operation and Big O Notation](#expensive-operation-and-big-o-notation)**
1.  **[Algorithms](#algorithms)**
1.  **[Inheritance, Polymorphism and Code Reuse](#inheritance-polymorphism-and-code-reuse)**
1.  **[Design Patterns](#design-patterns)**
1.  **[Partial Applications, Currying, Compose and Pipe](#partial-applications-currying-compose-and-pipe)**
1.  **[Clean Code](#clean-code)**

---

## Call Stack
...
**[? ����](#����)**

---

## Primitive Types
*  Number
*  String
*  Boolean
*  Null
*  Undefined
*  Symbol
### Number
#### ����
```javascript
var decimalNum = 100; // �⺻ ���� ���ͷ� ���� 10������ �ʱ�ȭ
var octalNum = 010; // 8������ �ʱ�ȭ
var hexNum = 0x10; // 16������ �ʱ�ȭ
```
#### �ε��Ҽ���
```javascript
var floatNum1 = 3.14;
var floatNum2 = 3.125e7;
```
##### �ε��Ҽ��� ��Ģ���� ����Ȯ
0.1 + 0.2 ����� 0.30000000000000004�� �Ʒ� �ڵ�� �ǵ���� �������� �ʴ´�.
```javascript
var f1 = 0.1;
var f2 = 0.2;

if (f1 + f2 == 0.3) {
    do_something();
}
```
#### ���� ����
*  �ּҰ� : Number.MIN_VALUE (5e-324)
*  �ִ밪 : Number.MAX_VALUE (1.7976931348623157e+308)
*  �ּ�, �ִ븦 ����� ����� Infinity, ������ -Infinity�� ��ȯ�ȴ�.
#### NaN
*  Not-a-Number�� ���Ӹ�
*  ���� ���ڰ� �ƴ��� ���Ѵ�.
*  ���ڸ� 0���� ���� ��� ��� ���� NaN�̴�.
*  NaN == NaN�� false�̴�.
*  isNaN �Լ��� ����Ͽ� �˻��Ѵ�.
#### ���ڿ��� ���ڷ� ��ȯ�ϴ� �Լ�
*  Number()
*  parseInt()
*  parseFloat()

---

### String
*  �ؽ�Ʈ �����͸� ��Ÿ���µ� ����Ѵ�.
*  16��Ʈ ��ȣ���� ���� �� ��ҵ��� �����̴�.
*  String �� ���̴� String�� ������ �ִ� ����� �����̴�.
*  ���ڿ��� �����Ǹ�, �� ���ڿ��� ������ �� ����.
*  ���� ���ڿ��� String.substr(), String.concat() ���� method�� ���� ������(+)�� ����� ���ο� ���ڿ��� �����.
#### ���ڿ��� ��ȯ�ϴ� �Լ�
*  toString() method�� ���� �ش��ϴ� ���ڿ��� ��ȯ�Ѵ�.
```javascript
var hundred = 100;
var hundred_string = hundred.toString(); // ���ڿ� "100"
var is_true = true;
var is_true_string = is_true.toString(); // ���ڿ� "true"
var hex_num = 10;
var hex_num_string = hex_num.toString(16); // 16���� ���ڿ� "a"
```
*  String() �Լ��� null�̳� undefined�� ��� �����ϴ�. (*toString�� �Ұ���*)
```javascript
var im_null = null;
var im_null_string = String(im_null); // ���ڿ� "null"
var im_undefined = undefined;
var im_undefined_string = String(im_undefeind); // ���ڿ� "undefined"
```

---

### Boolean
�־��� ������ ������ �������� ��Ÿ���� �ڷ����̴�.
```javascript
1 < 2; // true
1 > 2; // false
3 === 3; // true
3 !== 3; // false
Number.isFinite(Infinity); // false
Number.isNaN(NaN); // true
'hello'.includes('ll'); // true
```

---

### Null
*  � ���� *�ǵ�������* ��������� ǥ���Ѵ�.
*  null ���� ���� ��ü ������ ��� ��ü�� ����Ű�� ���� �ʴ� �����̴�.
*  �Լ����� ���ϰ��� ��������� ��ġ�ϴ� ���� ���� ��쿡 null�� �����ϴ� ������ ����Ѵ�.
*  null�� undefined ����
```javascript
typeof null          // "object" (����ȣȯ ������ ���� "null"�� �ƴ�)
typeof undefined     // "undefined"
null === undefined   // false
null  == undefined   // true
null === null        // true
null == null         // true
!null                // true
isNaN(1 + null)      // false
isNaN(1 + undefined) // true
```

---

### Undefined
*  ������ �� ���� �Ҵ����� ���� ���� Ȥ�� ���� �־����� ���� �μ��� �ڵ����� �Ҵ�ȴ�.
```javascript
var x; // ���� �Ҵ����� �ʰ� ���� ����
console.log("x's value is", x) // "x's value is undefined" ���
```

---

### Symbol
*  ECMAScript 2015���� ���� ������ ���� Ÿ���̴�.
*  ���� function/object�� Symbol�� ȣ���ϸ� Ÿ���� symbol�� �ȴ�.
```javascript
var mySymbol = Symbol(); // typeof mySymbol -> "symbol"
```
*  Symbol�� ��new�� Ű���带 ������� �� �Ѵ�.
```javascript
var mySymbol = new Symbol(); //throws error
```
*  Symbol�� description�� ������.
```javascript
// mySymbol variable now holds a "symbol" unique value
// its description is "some text"
var mySymbol = Symbol('some text');
```
*  Symbol�� unique�ϴ�.
```javascript
var mySymbol1 = Symbol('some text');
var mySymbol2 = Symbol('some text');
mySymbol1 == mySymbol2 // false
```
*  Symbol.for�� ����ϸ� Symbol�� �̱���ó�� �۵��Ѵ�.
```javascript
var mySymbol1 = Symbol.for('some key'); //creates a new symbol
var mySymbol2 = Symbol.for('some key'); // **returns the same symbol
mySymbol1 == mySymbol2 //true
```
*for �޼��带 ����ϴ� ������ � �Ѱ����� Symbol�� ����� �ٸ� ������ ���� Symbol�� �����ϱ� ���ؼ��̴�.*
*  Symbol�� ��ü ������Ƽ Ű�� �� �ִ�.
��ü�� Symbol�� �Ӽ�Ű�� ���� �� �ִ�. Symbol�� unique �ϱ� ������ �̸� �浹���� ��ü�� �Ӽ��� ��� �߰��� �� �ִ�.
```javascript
var mySymbol = Symbol("some car description");
var myObject = { name: 'bmw' };
myObject[mySymbol] = 'This is a car';
console.log(mySymbol); // Symbol(some car description)
console.log(myObject[mySymbol]); // This is a car
console.log(myObject.mySymbol); // x
```
**[? ����](#����)**

---

## Value Types and Reference Types
...
**[? ����](#����)**

---

## Implicit, Explicit, Nominal, Structuring and Duck Typing
### Type Coersion
```
true + false
==> 1 + 0
==> 1

`+` �����ڰ� true�� false�� numeric conversion�Ѵ�.  
```
```
12 / '6'
==> 12 / 6
==> 2

`/` �����ڰ� string '6'�� numeric conversion�Ѵ�.
```
```
"number" + 15 + 3 
==> "number15" + 3 
==> "number153"

`+` �����ڴ� �¿��� ��� �����Ѵ�. 
�׷��� "number"�� 15�� ���� ����Ǵµ� `+` �����ڰ� ���� 15�� string conversion�Ѵ�.  
�� ��� "number15"�� �ǰ� �ٽ� ���� 3�� string conversion�ȴ�.
```
```
15 + 3 + "number" 
==> 18 + "number" 
==> "18number"

15 + 3�� 18�� ���ǰ� `+` �����ڰ� 18�� string conversion�Ѵ�.
```
```
[1] > null
==> '1' > 0
==> 1 > 0
==> true

`>` �����ڰ� [1]�� null�� numeric conversion�� �Ѵ�.
```
```
"foo" + + "bar" 
==> "foo" + (+"bar") 
==> "foo" + NaN 
==> "fooNaN"

���� ������ `+` �����ڰ� ���� ������ ���� ������ +"bar"�� ���� �򰡵ȴ�.  
�׸��� ���� `+` �����ڰ� NaN�� string conversion�Ѵ�.
```
```
'true' == true
==> NaN == 1
==> false

false == 'false'   
==> 0 == NaN
==> false

`==` �����ڴ� numeric conversion�� �Ѵ�. 'true'�� NaN����, true�� 1�� ��ȯ�ȴ�.
```
```
null == ''
==> false

`==` �����ڴ� ���� numeric conversion�� ������, null�� �Բ� �� ���� �׷��� �ʴ�.  
null�� null�̳� undefined�� ���� ���� �ٸ� ��� �͵���� �ٸ���.
```
```
!!"false" == !!"true"  
==> true == true
==> true

`!!` �����ڴ� 'true'�� 'false' ���ڿ��� �� �� �� ���ڿ��� �ƴϱ� ������ true�� ��ȯ�Ѵ�.  
```
```
['x'] == 'x'  
==> 'x' == 'x'
==>  true

`==` �����ڴ� Array�� ���� numeric conversion�� �Ѵ�. 
Array�� `valueOf()` method�� Array �ڽ��� �����ϴµ� �װ��� ���ð�(primitive)�� �ƴϱ� ������ ���õȴ�.  
Array�� `toString()`�� ['x']�� 'x' ���ڿ��� ��ȯ�Ѵ�.
```
```
[] + null + 1  
==>  '' + null + 1  
==>  'null' + 1  
==> 'null1'

`+` �����ڴ� []�� numeric conversion�Ѵ�. Array�� `valueOf()` method�� �� �ڽ��� �����ϱ� ������ ���õȴ�.  
Array�� `toString()`�� �� ���ڿ��� �����Ѵ�.
```
```
0 || "0" && {}  
==>  (0 || "0") && {}
==> (false || true) && true  // internally
==> "0" && {}
==> true && true             // internally
==> {}

�� `||`, `&&` �����ڴ� �ǿ����ڸ� ���������� boolean���� ��ȯ�Ѵ�. 
������ ������ boolean�� �ƴ� ���� �ǿ����ڸ� �����Ѵ�.  
```
```
[1,2,3] == [1,2,3]
==>  false

�ǿ����ڵ��� ���� Ÿ���̱� ������ ����ȯ�� �ʿ����. 
�׷��� `==` �����ڴ� ������ object���� Ȯ���Ѵ�. (object�� ������ ������ Ȯ���ϴ� ���� �ƴϴ�.)  
�� �� Array�� ������ �ٸ� �ν��Ͻ��̱� ������ ���� �ʴ�. 
```
```
{}+[]+{}+[1]
==> +[]+{}+[1]
==> 0 + {} + [1]
==> 0 + '[object Object]' + [1]
==> '0[object Object]' + [1]
==> '0[object Object]' + '1'
==> '0[object Object]1'

��� �ǿ����ڰ� ���ð��� �ƴϴ�.  �׷��� `+` �����ڴ� ���ʺ��� numeric conversion�� �Ѵ�.  
ù ��° {}�� object ���ͷ��� �ƴ� ��Ϲ����� ó���Ǿ� ���õȴ�. 
�׷��� +[] ǥ������ �򰡵Ǵµ� `toString()` method�� ���� �� ���ڿ��� ��ȯ�ǰ� �� ���� 0���� �ȴ�.
```
```
!+[]+[]+![]  
==> (!+[]) + [] + (![])
==> !0 + [] + false
==> true + [] + false
==> true + '' + false
==> 'truefalse'

������ �켱 ������ ���� ó���ȴ�.
```
```
new Date(0) - 0
==> 0 - 0
==> 0

`-` �����ڴ� Date�� numeric conversion�Ѵ�. `Date.valueOf()`�� Unix epoch���� �и��ʸ� �����Ѵ�.
```
```
new Date(0) + 0
==> 'Thu Jan 01 1970 02:00:00 GMT+0200 (EET)' + 0
==> 'Thu Jan 01 1970 02:00:00 GMT+0200 (EET)0'

`+` �����ڴ� default conversion�� �Ѵ�. Date�� string conversion�� default�� `toString()` method�� ���ȴ�.
```

---

### Nonimal Typing
C++, Java, Swift ���� ������ �ֿ� nominal type system�̴�.
```javascript
class Foo { method(input: string) { /* ... */ } }
class Bar { method(input: string) { /* ... */ } }

let foo: Foo = new Bar(); // Error!
```
Ŭ���� �̸��� �ٸ� ������ �����Ϸ��� �� �� ������ �߻��Ѵ�.

---

### Structural Typing
OCaml, Haskell, Elm ���� ������ �ֿ� structural type system�̴�.
```javascript
class Foo { method(input: string) { /* ... */ } }
class Bar { method(input: string) { /* ... */ } }

let foo: Foo = new Bar(); // Works!
```
structure�� �Ϻ��ϰ� ���� Ŭ������ �̸��� �޶� ������ �����ϴ�.  
�׷��� Ŭ���� ������ �����ϸ� ������ �߻��Ѵ�.  
```javascript
class Foo { method(input: string) { /* ... */ } }
class Bar { method(input: number) { /* ... */ } }

let foo: Foo = new Bar(); // Error!
```

---

### Duck Typing
*  Duck Typing�� ���ڰ� � ������ ��� ���� �� ������ �� �� �ִ����� Ȯ���Ͽ� ��ü�� �Ǵ��ϴ� ����̴�. 
*  "����ó�� �Ȱ�, ����ó�� �Ҹ� ���� ������ �����Ѵ�(If it walks like a duck and quacks like a duck, I would call it a duck.)"�� ������ �����ߴ�.
�Ʒ��� �ڵ� �޽� ��ġ�� Javascript�� ������ �����̴�. �ڵ� �޽� ��ġ �տ��� "��" �Ҹ��� ����, �� quack() method�� �����ϸ� ���̸� �����Ѵ�.
```javascript
function FeedDispenser() {}; 
FeedDispenser.prototype.requestFeed = function(quackable) {
    return (quackable.quack() != null) ? new Feed() : null; 
};
```

������ Goose ��ü�� ������ �����̴�.
```javascript
function Goose() {};
Goose.prototype.honk = function() {
    return honk();
}
```

������Ÿ�� ��ü�� quack() �޼��带 �߰��� �����Ѵ�.
```javascript
Goose.prototype.quack = function() {
    return this.honk(); 
}
```

���� ���� Ȯ��� Goose �ν��Ͻ��� �ڵ� �޽� ��ġ�� �����ϸ� ������ ����.
```javascript
var goose = new Goose();
var feedDispenser = new FeedDispenser();
var feed = feedDispenser.requestFeed(goose);
console.log(feed != null); // true
```
**[? ����](#����)**

---

## == vs === vs typeof
...
**[? ����](#����)**

---

## Function Scope, Block Scope and Lexical Scope
###  Global Scope  
Javascript document���� ���� �ϳ��� global scope�� �����Ѵ�.  
�Լ� �ٱ��� ���ǵ� ������ global scope�� ���Ѵ�.
```javascript
// the scope is by default global
var name = 'msahn';
```
```javascript
var name = 'msahn';

console.log(name); // logs 'msahn'

function logName() {
    console.log(name); // 'name' is accessible here and everywhere else
}

logName(); // logs 'msahn'
```

---

### Local Scope  
�Լ� �ȿ��� ���ǵ� ������ local scope�� ���Ѵ�.
```javascript
// Global Scope
function someFunction() {
    // Local Scope #1
    function someOtherFunction() {
        // Local Scope #2
    }
}

// Global Scope
function anotherFunction() {
    // Local Scope #3
}
// Global Scope
```

---

### Block statements
Block statement�� function�� �޸� `if`�� `switch` ���� condition���̳� `for`�� `while`���� loop���̴�.
```javascript
if (true) {
    // this 'if' conditional block doesn't create a new scope
    var name = 'msahn'; // name is still in the global scope
}

console.log(name); // logs 'msahn'
```
```javascript
if (true) {
    // this 'if' conditional block doesn't create a scope

    // name is in the global scope because of the 'var' keyword
    var name = 'msahn';
    // likes is in the local scope because of the 'let' keyword
    let likes = 'Coding';
    // skills is in the local scope because of the 'const' keyword
    const skills = 'JavaScript';
}

console.log(name); // logs 'msahn'
console.log(likes); // Uncaught ReferenceError: likes is not defined
console.log(skills); // Uncaught ReferenceError: skills is not defined
```

---

### Lexical Scope  
lexical scope�� �������� �Լ� �׷��� �ǹ��Ѵ�.  
������ �Լ��� �� �θ� scope�� ������ resource�� ������ �����ϴ�.
```javascript
function grandfather() {
    var name = 'msahn';
    // likes is not accessible here
    function parent() {
        // name is accessible here
        // likes is not accessible here
        function child() {
            // Innermost level of the scope chain
            // name is also accessible here
            var likes = 'Coding';
        }
    }
}
```

**[? ����](#����)**

---

## Expression vs Statement
...
**[? ����](#����)**

---

## IIFE, Modules and Namespaces
### IIFE (Immediately-Invoked Function Expressions)
*  IIFE�� ���ǿ� ���ÿ� ȣ��Ǵ� �Լ��̴�.
```javascript
(function sayHi() {
        alert('Hi there!'); 
    }
)(); 
// alerts 'Hi there!'
```
*  IIFE�� ���� �����ϱ�
```javascript
(function (name) { 
        alert(`Hi, ${name}`); 
    }
)('Kim'); 
// alerts 'Hi, Kim'
```
*  IIFE�� �ֿ� ��� �뵵�� private scope�� ����� ���ؼ� �̴�. �ٽ� ���� ������ �ڵ尡 global scope�� �������� ���� �����ϰ� ���� ������ �ܺο��� �������� �� �ϵ��� ��ȣ�ϱ� ���ؼ� �̴�.  
�Ʒ��� ��ư Ŭ�� ���� ���� �����̴�.
```html
<!-- button.html --> 
<html>
    <body>
        <button id='button'>Click me!</button>
        <script src='button.js'>
        </script> 
    </body>
</html>
```
```javascript
// button.js
const button = document.getElementById('button');

button.addEventListener('click', (function() {
    let count = 0;
    return function() {
        count += 1;

        if (count === 2) {
            alert('This alert appears every other press!');
            count = 0;
        }
    };
})());
```
*  Ư���� ���� context�� �����ϱ� ���� ���� �� �� ����Ǵ� �ǵ��� ���ȴ�.
*  ES5������ ������ scope�� function�� ���ؼ��� ������ �� �־��� ������ ��� �Ǿ���. ES6���ʹ� let, const, module�� ��ü�� �� �ִ�.

---

### Modules
*  Ŭ���̾�Ʈ ���̵� �ڹٽ�ũ��Ʈ�� script �±׸� ����Ͽ� �ܺ��� ��ũ��Ʈ ������ ������ ���� ������, ���ϸ��� �������� ���� �������� ���� �ʰ� �ϳ��� ���� ��ü(Global Object)�� �����Ѵ�.
*  ���� ���̵� �ڹٽ�ũ��Ʈ ��Ÿ�� ȯ���� Node.js�� ��� �ý����� ��ǻ� ǥ��(de facto standard)�� CommonJS�� ä���Ͽ��� �������� ��ȭ�� ���� ����� CommonJS ���� 100% ���������� ������ �⺻������ CommonJS ����� ������ �ִ�.
*  ES6������ Ŭ���̾�Ʈ ���̵� �ڹٽ�ũ��Ʈ������ �����ϴ� ��� ����� �߰��Ͽ���. 2019�� 11�� ����, ��� ������(Chrome 61, FF 60, SF 10.1, Edge 16 �̻�)���� ES6 ����� ����� �� �ִ�.
*  script �±׿� type="module" ��Ʈ����Ʈ�� �߰��ϸ� �ε�� �ڹٽ�ũ��Ʈ ������ ���μ� �����Ѵ�. ES6 ����� ���� Ȯ���ڴ� ������� ��Ȯ�� �ϱ� ���� mjs�� ����ϵ��� �����Ѵ�.
```html
<script type="module" src="lib.mjs"></script>
<script type="module" src="app.mjs"></script> 
```
*  ��, �Ʒ��� ���� ������ ���������� �������� �����ϴ� ES6 ��� ��ɺ��ٴ� Webpack ���� ��� ���鷯�� ����ϴ� ���� �Ϲ����̴�.
    *  IE�� ������ ���� �������� ES6 ����� �������� �ʴ´�.
    *  �������� ES6 ��� ����� ����ϴ��� Ʈ�������ϸ��̳� ���鸵�� �ʿ��ϴ�.
    *  ���� �������� �ʴ� ���(Bare import ��)�� �ִ�.
    *  ���� �ذ�ǰ�� ������ ���� ��� �̽��� �ִ�.

---

### Namespaces
*  Namespace ������ ���� ������ ������ �����ϰ� �ڵ带 ����ϴ� ���� �����ϱ� ���� ���ӽ����̽���� �и��� ������ ����� �� �ȿ��� ������ �����ϰ� �ڵ带 �ۼ��ϵ��� �ϴ� �����̴�.
*  Namespace ����
```javascript
var NAMESPACE = {}; // ���ӽ����̽� ����

NAMESPACE.number = 1; // ���� ����
NAMESPACE.func = function() {}; // �Լ� ����
NAMESPACE.obj = {}; // ��ü ����
``` 
*  Namespace �̸��� �浹 ������ ���� ��� �빮�ڸ� ����Ѵ�.
*  ��� ������ �Լ��� ���ξ �ٿ��� �ϱ� ������ ��ü������ �ڵ差�� �ణ �� �������� ���� ���� ũ�⵵ �þ��.
*  �̸��� ��ø�ǰ� ������Ƿ� ������Ƽ�� �Ǻ��ϱ� ���� �˻� �۾��� ��� ��������. 

**[? ����](#����)**

---

## Message Queue and Event Loop
...
**[? ����](#����)**

---

## setTimeout, setInterval and requestAnimationFrame
### setTimeout
*  setTimeout �Լ��� ������ �ð���ŭ ��ٸ� �� �� �ѹ� ������ �Լ��� �����Ѵ�.
*  �����Ϸ��� clearTimeout�� ȣ���Ѵ�.
```javascript
/* ���� */
var loopTimer = setTimeout(function(){ /* process... */}, delay);
/* ���� */
clearTimeout(loopTimer);
```
*  setTimeout �Լ��� �� �ѹ� ������ �Լ��� ���������� ��� ȣ���� ���� �ݺ������� ���� �� �� �ִ�.
*  ���� delay�� 100ms�� �����ߴٸ� ������ �Լ��� ����Ǵ� ������ 100ms �̻��̴�.
![settimeout](./img/settimeout.PNG)

### setInterval
*  setInterval �Լ��� ������ �ð���ŭ ��ٸ� �� ������ �Լ��� �����ϰ� �� ������ �ݺ��Ѵ�.
*  �����Ϸ��� clearInterval�� ȣ���Ѵ�.
```javascript
/* ���� */
var onceTimer = setInterval(function(){ /* process... */ }, delay); 
/* ���� */
clearInterval(onceTimer);
```
*  �������� �Լ��� ������ �� ���� ����(busy)��� �̺�Ʈ�� �ִ� ���̰� 1�� ť�� �����Ѵ�.
*  ť�� �̹� �̺�Ʈ�� �����Ѵٸ� �� �̺�Ʈ�� skip �ȴ�.
*  ���� delay�� 100ms�� �����ߴٸ� ���� delay�� 100ms���� ����.
![setinterval](./img/setinterval.PNG)

### setTimeout, setInterval limitations
*  �������� setTimeout�� 5�� �̻��� ��ø ȣ�� �Ǵ� setInterval(5 ��° ȣ�� ����)�� ���� �ּ� ������ 4ms�� �����Ѵ�. (historical reason?)
*  ������ ���� Ÿ�̸Ӵ� ���� ������� ���� ������ �� �ִ�.
    *  CPU ������
    *  �귯���� ���� ��׶��� ��忡 ���� ��
    *  ��ž�� ���͸��� ��� �� �� ��

### requestAnimationFrame
*  ���������� javascript���� �ִϸ��̼��� ���� ���� setTimeout�̳� setInterval�� ����߾���.
```js
var adiv = document.getElementById('mydiv')
var leftpos = 0
setInterval(function(){
    leftpos += 5
    adiv.style.left = leftpos + 'px' // move div by 5 pixels each time
}, 50) // run code every 50 milliseconds
```
*  �� �ڵ�� �������� �׷��� ������ ���� ������ �Ϻ����� �ʴ�. ������ ������ ����.
    *  �ý��� ���ҽ� �������� ���� ���� ������ �������� �ʴ�.
    *  ȭ���� ���������� �����ϱ� ���� �����ϰ� setTimeout, setInterval�� ����ϸ� layout thrashing���� ���� ���� ���ϰ� ���ߵȴ�.
*  requestAnimationFrame method�� ���� ȭ���� ���ŵǾ� ǥ�õǴ� �ֱ⿡ ���� �Լ��� ȣ�����ֱ� ������ �ڹٽ�ũ��Ʈ�� ������ ���� �� ����ǵ��� �����Ѵ�.
*  ���� 1�ʿ� 60ȸ ���� ������ ������ ��κ��� �������� W3C ������׿� ���� ���÷��� �ֻ����� ��ġ�ϵ��� ����ȴ�.
*  requestAnimationFrame()�� ���� â�� ǥ�� ���� ������ �ִϸ��̼��� �����Ѵ�.
```js
var adiv = document.getElementById('mydiv')
var leftpos = 0
requestAnimationFrame(function(timestamp){
    leftpos += 5
    adiv.style.left = leftpos + 'px'
})
```
**[? ����](#����)**

---

## JavaScript Engines
...
**[? ����](#����)**

---

## Bitwise Operators, Type Arrays and Array Buffers
### Bitwise Operators
������ | ���� | ����
---|---|--
Bitwise AND|a & b|���ʰ� ������ �ǿ������� ��Ʈ�� 1�̸� �� ��Ʈ�� 1�� ����
Bitwise OR|a | b|�����̳� ������ �ǿ������� ��Ʈ�� 1�̸� �� ��Ʈ�� 1�� ����
Bitwise XOR|a ^ b|�����̳� ������ �ǿ������� ��Ʈ �� �� �ʸ� 1�̸� �� ��Ʈ�� 1�� ����
Bitwise NOT|~ a|�ǿ������� ��� ��Ʈ�� ���� ��Ŵ
Left shift|a << b|a�� �����ʿ��� �������� b ��Ʈ ��ŭ �̵� ��Ű�� 0���� ä��
Sign-propagating right shift|a >> b|a�� ���ʿ��� ���������� b ��Ʈ ��ŭ �̵� ��Ű�� ����� ��� 0����, ������ ��� 1�� ä��
Zero-fill right shift|a >>> b|a�� ���ʿ��� ���������� b ��Ʈ ��ŭ �̵� ��Ű�� 0���� ä��
  
### Type Arrays and Array Buffers
*  ����(raw) ���� ������ �������� ���� ��ü
*  ���ۿ� ��� ������ ��
*  ����(ArrayBuffer ��ü�� ���� ������)�� ������ �κ�(chunk, ���)�� ��Ÿ���� ��ü
*  ����ȭ �迭 ��

�̸� | ���� | ���� | Ÿ��
---|---|---|---
Int8Array|-128 ~ 127|��ȣ�ִ� 8��Ʈ ����|char
Uint8Array|0 ~ 255|��ȣ���� 8��Ʈ ����|unsigned char
Int16Array|-32,768 ~ 32,767|��ȣ�ִ� 16��Ʈ ����|short
Uint16Array|0 ~ 65,535|��ȣ���� 16��Ʈ ����|unsigned short
Int32Array|-2,147,483,648 ~ 2,147,483,647|��ȣ�ִ� 32��Ʈ ����|int
Uint32Array|0 ~ 4,294,967,295|��ȣ���� 32��Ʈ ����|unsigned int
Float32Array|-3.4 x 10�� 38�� ~ 3.4 x 10�� 38��|32-bit IEEE floating point number|float
Float64Array|-1.79 x 10�� 308�� ~ 1.79 x 10�� 308��|64-bit IEEE floating point number|double

![typed_arrays](./img/typed_arrays.png)

*  ��� ���ۿ� �����͸� �аų� �� �� �ִ� getter/setter API�� �����ϴ� ������ �������̽�
*  ���� ���
```js
var buffer = new ArrayBuffer(16);

if (buffer.byteLength === 16) {
  console.log("Yes, it's 16 bytes.");
} else {
  console.log("Oh no, it's the wrong size!");
}
```
*  �� ���
```js
var buffer = new ArrayBuffer(16);

var int32View = new Int32Array(buffer);

for (var i = 0; i < int32View.length; i++) {
  int32View[i] = i * 2;
}


var int16View = new Int16Array(buffer);

for (var i = 0; i < int16View.length; i++) {
  console.log("Entry " + i + ": " + int16View[i]);
}

```

*  C ��� ����ü�� �۾�
```c
  struct someStruct {
  unsigned long id;
  char username[16];
  float amountDue;
};
```
```js
var buffer = new ArrayBuffer(24);

// ... ���� ���� �����͸� �о���� ...

var idView = new Uint32Array(buffer, 0, 1);
var usernameView = new Uint8Array(buffer, 4, 16);
var amountDueView = new Float32Array(buffer, 20, 1);
```

**[? ����](#����)**

---

## DOM and Layout Trees
...
**[? ����](#����)**

---

## Factories and Classes
### Class�� ������ ToDo Model
```js
class TodoModel {
    constructor(){
        this.todos = [];
        this.lastChange = null;
    }
    
    addToPrivateList(){
        console.log("addToPrivateList"); 
    }
    add() { console.log("add"); }
    reload(){}
}
```
### Factory function���� ������ ToDo Model
```js
function TodoModel(){
    var todos = [];
    var lastChange = null;
        
    function addToPrivateList(){
        console.log("addToPrivateList"); 
    }
    function add() { console.log("add"); }
    function reload(){}
    
    return Object.freeze({
        add,
        reload
    });
}
```
### Encapsulation
*  Class�� ��� ���, �ʵ�, �޼���� public�̴�.
```js
var todoModel = new TodoModel();
console.log(todoModel.todos);     //[]
console.log(todoModel.lastChange) //null
todoModel.addToPrivateList();     //addToPrivateList
```
*  Factory function�� �޼��常 ����ǰ� ������ �ٸ� �͵��� ��� ��ȣ�ȴ�.
```js
var todoModel = TodoModel();
console.log(todoModel.todos);     //undefined
console.log(todoModel.lastChange) //undefined
todoModel.addToPrivateList();     //todoModel.addToPrivateList is not a function
```
### this
*  class�� ����� ���� this�� context�� �Ҵ� ������ �ִ�.
```js
class TodoModel {
    constructor(){
        this.todos = [];
    }
    
    reload(){ 
        setTimeout(function log() { 
           console.log(this.todos);    //undefined
        }, 0);
    }
}
todoModel = TodoModel();
todoModel.reload();
```
*  �� ������ callback�� ȭ��ǥ �Լ��� ����Ͽ� �ذ� �� �� �ִ�.
```js
class TodoModel {
    constructor(){
        this.todos = [];
    }
    
    reload(){ 
        setTimeout(() => { 
           console.log(this.todos);    //undefined
        }, 0);
    }
}
todoModel = TodoModel();
todoModel.reload();
```
*  Factory function�� this�� ������� �ʱ� ������ ������ ����.
```js
function TodoModel(){
    var todos = [];
        
    function reload(){ 
        setTimeout(function log() { 
           console.log(todos);        //[]
       }, 0);
    }
}
todoModel = TodoModel();
todoModel.reload();
```
**[? ����](#����)**

---

## this, call, apply and bind
...
**[? ����](#����)**

---

## new, Constructor, instanceof and Instances
### new
new �����ڸ� ���� �����ڴ� user-defined object type�� ������ �Լ��� �ִ� built-in object type�� �ν��Ͻ��� ���� �� �ִ�.  
new Ű����� ������ �����Ѵ�.  

*  ���ο� object�� ���������.
*  this�� �� object�� �����Ѵ�.
*  ������ �Լ��� prototype object�� �� object�� ```__proto__``` property�� �ȴ�.
*  �Լ��κ��� object�� �����Ѵ�.

#### ES5 class
```js
function User(name, points) {
  this.name = name; 
  this.points = points;
}
User.prototype.increment = function(){
  this.points++;
}
User.prototype.login = function() {
  console.log(��Please login.��)
}

let user1 = new User(��Dylan��, 6);
user1.increment();
```
#### ES6 class
```js
class User {
  constructor(name, points) {
    this.name = name;
    this.points = points;
  }
  increment () {
    this.points++;
  }
  login () {
    console.log("Please login.")
  }
}

let user1 = new User("John", 12);
user1.increment();
```
#### �� object�� new�� �����ؾ� �ϴ� ����
````js
var userProfile = function(name, age) {
    this.userName = name;
    this.userAge = age;
    return this;
};

var user = userProfile('uyeong', 27);
console.log(user === window); // true
console.log(window.userName); // uyeong
console.log(window.userAge); // 27
delete user; // true
delete window.userName; // true
delete window.userAge; // true

var user = new userProfile('uyeong', 27);
console.log(user === window); // false
console.log(window.userName); // undefined
console.log(window.userAge); // undefined
console.log(user.userName); // uyeong
console.log(user.userAge); // 27
````

### instance
*  object�� ���� ������ ��ü�� ���α׷������� ǥ���� ���̴�.
````js
var person = {
  name: 'Juan',
  age: 40,
  gender: 'male',
  greeting: function() {
    alert('Hi! I\'m ' + this.name + '.');
  }
};
````
*  �� object�� ����ϱ� ���� �� object�� instance�� �����ؾ� �Ѵ�.
```js
var guy = new person();
````
*  �� ��ɾ� �������� person type�� object�� ������ �� �ִ� �޸𸮰� �Ҵ� �� �ʱ�ȭ �ǰ� �� instance�� ���� �� �� �ִ� guy ������ ����� ����.

### instanceof
*  instanceof �� �� �������̴�.
*  �ش� ������ ����ϰ� �ִ� prototype�� chain�� �� ��° ���ڿ� �� ���ؼ� true�� false�� �����Ѵ�.
*  ��� object�� �⺻ object�� Object�� Ȯ���ϱ� ������ instanceof Object�� true�̴�.
```js
var Person = function(){ 
    this.name = "unikys"; 
}; 

var inst = new Person(); 
inst instanceof Person; // === true 
inst instanceof Object; // === true 
typeof inst; // === 'object'
```
*  primitive type���� ����� �� ����.
```js
"foo" instanceof String; // === false 
"foo" instanceof Object; // === false 
true instanceof Boolean; // === false 
true instanceof Object; // === false 

[0,1] instanceof Array; // === true 
{0:1} instanceof Object; // === true 

var color1 = new String("red"); 
var color2 = "red"; 
color1 == color2; // === true 
color1 instanceof String; // === true 
color2 instanceof String; // === false
```

**[? ����](#����)**

---

## Prototype Inheritance and Prototype Chain
...
**[? ����](#����)**

---

## Object.create and Object.assign
### Object.create
*  �־��� prototype object�� property�� ���ο� object�� �����.
*  ����� ������ �� ����Ѵ�.
```
Object.create(prototype[, propertiesObject])
```
```js
function fruits() {
    this.name = 'fruit 1';
}

function apple() {
    fruits.call(this);
}

apple.prototype = Object.create(fruits.prototype);
const app = new apple();
console.log(app.name);  // "fruit 1"
```
### Object.assign
*  ������ �� �ִ� �ϳ� �̻��� source object�κ��� target object�� �Ӽ��� ������ �� ����Ѵ�.
```js
var obj1 = { a: 10, b: 10, c: 10 };
var obj2 = { b: 20, c: 20 };
var obj3 = { c: 30 };

var new_obj = Object.assign({}, obj1, obj2, obj3);

console.log(new_obj);  // Object { a: 10, b: 20, c: 30 }
```
**[? ����](#����)**

---

## map, reduce, filter
...
**[? ����](#����)**

---

## Pure Functions, Side Effects and State Mutation
...
**[? ����](#����)**

---

## Closures
...
**[? ����](#����)**

---

## High Order Functions
...
**[? ����](#����)**

---

## Recursion
...
**[? ����](#����)**

---

## Collections and Generators
...
**[? ����](#����)**

---

## Promises
...
**[? ����](#����)**

---

## async/await
...
**[? ����](#����)**

---

## Data Structures
...
**[? ����](#����)**

---

## Expensive Operation and Big O Notation
...
**[? ����](#����)**

---

## Algorithms
...
**[? ����](#����)**

---

## Inheritance, Polymorphism and Code Reuse
...
**[? ����](#����)**

---

## Design Patterns
...
**[? ����](#����)**

---

## Partial Applications, Currying, Compose and Pipe
...
**[? ����](#����)**

---

## Clean Code
...
**[? ����](#����)**

---