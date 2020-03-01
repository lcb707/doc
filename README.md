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
*  call stack(ȣ�� ����)�� ���α׷����� �츮�� ��� �ִ� ���� �⺻������ ����ϴ� ������ �����̴�.
*  �ڹٽ�ũ��Ʈ�� single-thread ���α׷��� ����̹Ƿ�, �ϳ��� ȣ�� ������ �ִ�.
*  �Լ��� �����ϸ� �ش� �Լ��� ����� ���� �� ���� �߰�(push)�Ѵ�.
*  �Լ��� ���ϵǸ� ���ÿ� �׿��ִ� �Լ��� ����(pop)�ȴ�.
### �Լ� ����, ���� �� ȣ�� ���� ����
```js
function multiply(x, y) {
    return x * y;
}
function printSquare(x) {
    var s = multiply(x, x);
    console.log(s);
}
printSquare(5);
```
![callstack](./img/callstack_ex1.PNG)
### ���� ó�� �� ������ ����
```js
function foo() {
    throw new Error('SessionStack will help you resolve crashes :)');
}
function bar() {
    foo();
}
function start() {
    bar();
}
start();
```
![callstack2](./img/callstack_ex2.PNG)
### Stack Overflow
������ ����� �ʰ� ���� �� �߻��ϴ� �����̴�. �Ʒ��� ���� ��� ȣ�� �� �߻� ��ų �� �ִ�.
```js
function foo() {
    foo();
}
foo();
```
### ���� ȣ�� ������ ������
�ϳ��� �Լ� ������ ������ ��� �ٸ� �Լ� ������ �ʾ����� ������ �ִ�.

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
### Value Types
*  �ڹٽ�ũ��Ʈ�� ���� ���� ����(passed by value)�� �Ͼ�� 6������ ������ Ÿ��(Boolean, Null, Undefined, String, Number, Symbol)�� ������ �ִ�. 
*  �̷��� ������ Ÿ���� ���� Ÿ��(Primitive Types)�̶�� �θ���.
*  ��� ���� Ÿ���� ������ �Ҵ� �ȴٸ�, �� ������ ���� Ÿ���� ���� ������� ������ �� �ִ�.
```js
var x = 10;
var y = 'abc';
var z = null;
```
*  ������ x�� 10�̶� ���� ������ �ְ�, y�� abc�� ���� ������ �ִ�.
*  �� �������� �ٸ� ������ `=` Ű���带 �̿��Ͽ� �Ҵ��� ��, ���ο� ������ ���� ����(copy)�ϰ� �ȴ�.
```js
var x = 10;
var y = 'abc';

var a = x;
var b = y;

console.log(x, y, a, b); // -> 10, 'abc', 10, 'abc'
```
*  ������ a�� x�� �� �� 10�̶� ���� ���� �ȴ�. 
*  b�� y�� �� �� abc��� ���� ���� �ִ�.
*  �̵��� ������ ���� �� ���̱� ������ ������ �������� ���� ���谡 ����.

### Reference Types
*  �ڹٽ�ũ��Ʈ�� ������ ���� ����(passed by reference)�� �Ͼ�� 3���� ������ Ÿ��(Array, Function, Object)�� ������ �ִ�.
*  �� 3���� ������ Ÿ���� ũ�� ���� ���� ��ü(Object)�� �� �� �ִ�.
*  ���� Ÿ���� �ƴ� ���� �Ҵ�� �������� �� ������ ���ϴ� ����(reference)�� ���� �ȴ�.
*  ����(reference)�� �޸𸮿��� ��ü�� ��ġ�� ����Ű�� �ִ�. ��, ������ ������ ���� ������ ���� �ʴ�.
*  `arr = []`�� �ۼ��ϸ� �޸𸮿� �迭�� �����ȴ�. ���� `arr`�� ���� ���� �� �迭�� ��ġ�� �ּ��̴�.
*  ��ü�� ���� ���� Ÿ���� ���� `=` Ű����� �ٸ� ������ ����� �� �� �ּҰ�(����)�� ����ȴ�. 
```js
var reference = [1];
var refCopy = reference;
```
*  �� ������ ���� �迭�� �����Ѵٴ� ���� �Ʒ��� ���� Ȯ���� �� �ִ�.
```js
reference.push(2);
console.log(reference, refCopy); // -> [1, 2], [1, 2]
```
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
### ==
`==` �����ڴ� ���� �����ڷ� �ǿ����ڰ� ���� �ٸ� Ÿ���̸� Ÿ���� ������ ��ȯ�Ͽ� ���Ѵ�.
```js
0 == ''     //true
0 == '0'     //true
1 == true     //true
false == '0'    //true
null == undefined    //true
false == null    //false
false == undefined    //false
```
### === 
`===` �����ڴ� ��ġ �����ڷ� �� �ǿ����ڸ� �� ��Ȯ�ϰ� ���Ѵ�.
```js
0 === ''     //false
0 === false    //false
1 === true     //false
NaN === NaN     //false
null === undefined     //false
```
### typeof
*  typeof�� ������ ������ Ÿ���� ��ȯ�ϴ� �������̴�.
*  ���� : typeof variable
*  ��ȯ�Ǵ� ��
	*  undefined : ������ ���ǵ��� �ʰų� ���� ���� ��
	*  number : ������ Ÿ���� ���� ��
	*  string : ������ Ÿ���� ���ڿ��� ��
	*  boolean : ������ Ÿ���� �Ҹ����� ��
	*  object : ������ Ÿ���� �Լ�, �迭 �� ��ü�� ��
	*  function : ������ ���� �Լ��� ��
	*  symbol : ������ Ÿ���� �ɺ��� ��
  
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
### Expression
*  Expression�̶� ���� �����س��� �ڵ带 ���Ѵ�.
*  ���� ����Ǳ� ������ �Լ��� ���ڷ� �� �� �ִ�.
```js
3;
'hello';
myVar;
5+5;
myFunc('a', 'b');
```
### Statement
*  Statement�� Ư�� �׼��� �����ϴ� �ڵ带 ���Ѵ�.
*  Statement�� ���� ������ �� ������ �̸� Expression Statement��� Ī�ϰ� �ȴ�.
*  Statement �߿��� if Statement�� for Statementó�� �� ��ü�δ� ���� �������� ���� �� �ְ� �̰͵��� �Լ��� ���ڷε� �� �� ����.
*  ��� Expression�� Statement������, ��� Statement�� Expression�� �ƴϴ�.
### Function Expression vs Function Statement
*  Function�� �Ʒ�ó�� Expression �� Statement �������� ����� �� �ִ�.
```js
// Function Expression
var greet = function() {
  console.log("Hello");
};

// Function Statement
function greet() {
  console.log("Hello");
}
```
*  greet() ���๮�� �Լ� ���� ���� �߰��� ��� Function Expression�� undefined�� ����ǰ�, Function Statement�� Hello�� ��µȴ�.  

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
### ���������� �ڹٽ�ũ��Ʈ ��Ÿ�� ȯ��
![js_event_loop](./img/js_event_loop.png)  
*  Heap  
  ������ �ڹٽ�ũ��Ʈ ��ü�� �����ϴ� �޸�
*  Stack(Call Stack)  
  ���� ���α׷��� �����ϰ� �ִ� �۾��� ����ϴ� �ڷ� ����
*  Web APIs  
  Document, AJAX, Event, Timing �� �ھ� �ڹٽ�ũ��Ʈ�� ���� ����� �����Ѵ�. ���������� �����ϴ� ��ɵ��̴�. ��ǥ������ setTimeout�� �ִ�. ��� ���� �� callback�� Message Queue�� �߰��Ѵ�.
*  Message Queue(Callback Queue, Event Queue)  
  ó���ؾ� �ϴ� Event���� �ӽ� �����ϴ� ��� queue
*  Event Loop  
  Call Stack�� ������� �� Message Queue�� ����ϰ� �ִ� Event�� Call Stack�� push �ȴ�.
### Microtask, Microtask queue(Job queue)
![js_microtask](./img/js_microtask.png)
*  Microtask�� Macrotask���� �켱 ������ ����.
*  Macrotask�� �׻� JS �ڵ� ������ �Ϸ�ǰ� Microtask Queue�� ����ִ� �Ŀ� ����ȴ�.
*  JS �ڵ� ���� ��ü�� Macrotask�̴�.
*  Microtask ť�� ��� �� UI�� �ٽ� ������ �� �� �ִ�.
*  Promise�� Microtask�� ���ϰ� setTimeout�� Macrotask�� ���Ѵ�.
*  ���� ������ ������ ����. General code->Promises->Events and setTimeout etc.
*  �Ʒ� �ڵ��� ��� ���� : script start -> script end -> promise1 -> promise2 -> requestAnimationFrame -> setTimeout
```js
console.log("script start");

setTimeout(function() {
  console.log("setTimeout");
}, 0);

requestAnimationFrame(function() {
    console.log("requestAnimationFrame");
});

Promise.resolve().then(function() {
  console.log("promise1");
}).then(function() {
  console.log("promise2");
});

console.log("script end");
```
![js_microtask2](./img/js_microtask2.png)

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
### JavaScript Engine Pipeline
�ڹٽ�ũ��Ʈ ������ �ҽ� �ڵ带 ����� �������� ���������� �����ϴ� ����  
![js_engine_pipeline](./img/js_engine_pipeline.png)
1. �ҽ� �ڵ带 �Ľ��Ͽ� [Abstract Syntax Tree](https://ko.wikipedia.org/wiki/%EC%B6%94%EC%83%81_%EA%B5%AC%EB%AC%B8_%ED%8A%B8%EB%A6%AC)(AST)�� ����
2. ���������ʹ� AST�� �������� ����Ʈ�ڵ� ���� (�����δ� ��������� ������ �����ϴ� �κ�)
3. �ڵ带 �� ������ �����ϱ� ���� ����Ʈ �ڵ�� �������ϸ� �����͸� ����ȭ �����Ϸ����� ����
4. ����ȭ �����Ϸ��� �������ϸ� �����͸� ������� ����ȭ�� ��� ����
5. ��Ȯ���� ���� ����� ������ �ٽ� deoptimize�Ͽ� ����Ʈ �ڵ�� �ǵ���

![js_engine_optimizing](./img/js_engine_optimizing.png)
*  ����������(interpreter)  
  ����ȭ ���� ���� ����Ʈ �ڵ带 ������ �����Ѵ�.
*  ����ȭ �����Ϸ�(optimizing compiler)  
  ����ȭ�� ���� �ڵ带 �����Ѵ�.
*  �� �������� ����Ʈ �ڵ�� �߰� ���(IR: Intermediate Representation)�̴�. `interpreter` ����� ����Ʈ �ڵ带 �ϳ��� �о �����ϰ�, `JIT` ����� ����Ʈ �ڵ带 ������� �������Ͽ� �����Ѵ�.
*  ����Ʈ �ڵ�(Byte code)  
  Ư�� �ϵ��� �ƴ� ���� ��ǻ�Ϳ��� ���ư��� ���� ���α׷��� ���� ���� ǥ����. �ϵ��� �ƴ� ����Ʈ��� ���� ó���Ǳ� ������ ���� ����� �� �߻����̴�.
*  JIT ������(Just-In-Time Compilation) �Ǵ� ���� ����(Dynamic Translation)�� ���α׷��� ���� �����ϴ� ������ ����� �����ϴ� ������ ����̴�. �� ����� ���α׷��� ���� �ӵ��� ������ �ϱ� ���� ���ȴ�.
*  ���������ʹ� ����Ʈ �ڵ带 ������ ������ �� ������ ȿ������ �ڵ尡 �ƴϴ�. �ݴ�� ����ȭ �����Ϸ��� �ð��� ���� �� �ɸ����� ȿ������ ��� �ڵ带 �����Ѵ�.

![js_engine_pipleline-v8](./img/js_engine_pipleline-v8.png)
*  V8�� ���� ��Ʈ�� �̸� �״�� �ڵ����� 8���� ������ ����δ� ���̹��� �ϰ� �ִ�.
*  ���������ʹ� `Ignition`�̶�� �θ��� �ڵ带 ��ȭ�Ͽ� ����Ʈ �ڵ带 ���� �� �����Ѵ�.
*  ����Ʈ �ڵ尡 ����� �� ���������ʹ� �������ϸ� �����͸� �����Ͽ� ���߿� ����ȭ �� �� ����Ѵ�.
*  Ư�� �Լ��� ���� �����ϰ� �Ǹ� ����Ʈ �ڵ�� �������ϸ� �����͸� `TurboFan`�̶�� �θ��� ����ȭ �����Ϸ��� ������ ����ȭ�� ��� ������.


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
*  DOM�� ���� ��ü ��(Document Object Model)�� �����̴�.
*  DOM�� HTML element�� �������� �ٲٰ� �߰��ϰ� �����ϴ� ����� ���� ǥ���̴�.
*  DOM�� �ڷᱸ�� �� Ʈ��(Tree) ������ �ϰ� �ִ�.  
![htmltree.gif](./img/htmltree.gif)
*  Layout tree�� 4 ������ ���� �����ȴ�.
	*  ���� ���(Document Node)  
    Ʈ���� �ֻ����� �����ϸ� ���� ���, ��Ʈ����Ʈ, �ؽ�Ʈ ��忡 �����Ϸ��� ���� ��带 ���ؾ� �Ѵ�. ��, DOM tree�� �����ϱ� ���� ������(entry point)�̴�.
	*  ��� ���(Element Node)  
    ��� ���� HTML ��Ҹ� ǥ���Ѵ�. HTML ��Ҵ� ��ø�� ���� ���� ���踦 ������ �� ���� ���踦 ���� ������ ����ȭ�Ѵ�. ���� ��� ���� ������ ������ �����Ѵٰ� �� �� �� �ִ�. ��Ʈ����Ʈ, �ؽ�Ʈ ��忡 �����Ϸ��� ���� ��� ��带 ã�� �����ؾ� �Ѵ�. ��� ��� ���� ��Һ� Ư���� ǥ���ϱ� ���� HTMLElement ��ü�� ����� ��ü�� �����ȴ�.
	*  ��Ʈ����Ʈ ���(Attribute Node)  
    �Ӽ� ���� HTML ����� ��Ʈ����Ʈ�� ǥ���Ѵ�. ��Ʈ����Ʈ ���� �ش� ��Ʈ����Ʈ�� ������ ����� �ڽ��� �ƴ϶� �ش� ����� �Ϻη� ǥ���ȴ�. ���� �ش� ��� ��带 ã�� �����ϸ� ��Ʈ����Ʈ�� ����, ������ �� �ִ�.
	*  �ؽ�Ʈ ���(Text Node)  
    �ؽ�Ʈ ���� HTML ����� �ؽ�Ʈ�� ǥ���Ѵ�. �ؽ�Ʈ ���� ��� ����� �ڽ��̸� �ڽ��� �ڽ� ��带 ���� �� ����. ��, �ؽ�Ʈ ���� DOM tree�� �������̴�.
    
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
### this
*  ���� �Լ��� �θ� ��ü�� ���������� ��Ÿ����.
*  this�� �������� ������ �⺻������ �������� ������ü�� ����Ų��.
*  use strict ��忡���� this�� �������� �ʾ��� ��� undefined �� �����ȴ�.
*  ��ü�� �޼ҵ�� ȣ�� �Ǿ������� �ش� �޼ҵ��� ��ü�� ����Ų��.
*  ES6 ȭ��ǥ �Լ��� ����Ѵٸ� ������ ���ε��� �����ϰ� ������ �������� this�� ���ε� �ȴ�.

### call
*  call �޼���� ��� �Լ����� ����� �� ������, this�� Ư�� ������ ������ �� �ִ�.
```js
    const bruce = {
        name : 'Bruce'
    };

    const madeline = {
        name : 'Madeline'
    };

    //�� �Լ��� � ��ü���� ������� �ʾ����� this�� �����.
    function greet(){
        return `Hello, I'm ${this.name}`;
    };

    greet();               // 'Hello, I'm undefined' - this�� ��𿡵� ������ ����
    greet.call(bruce)     // 'Hello, I'm Bruce'     - this�� bruce
    greet.call(madeline)   // 'Hello, I'm Madeline'  - this�� madeline
```
*  �Լ��� ȣ���ϸ鼭 call�� ����ϰ� this�� ����� ��ü�� �ѱ�� �ش� �Լ��� �־��� ��ü�� �޼����� ��ó�� ����� �� �ִ�.
*  call�� ù ��° �Ű������� this�� ����� ���̰�, �Ű������� �� ������ �� �Ű������� ȣ���ϴ� �Լ��� ���޵ȴ�.
```js
    function update(birthYear, occupation){
        this.birthYear = birthYear;
        this.occupation = occupation;
    };

    update.call(bruce, 1949, 'singer'); // bruce ����
    /*
        bruce�� ����
        {
            name : 'Bruce',
            birthYear : 1949,
            occupation : 'singer'
        }
        �� �����
     */

    update.call(madeline, 1942, 'actress'); // madeline ����
    /*
        madeline�� ����
        {
            name : 'Madeline',
            birthYear : 1942,
            occupation : 'actress'
        }
        �� �����
     */
```
### apply
*  apply�� �Լ� �Ű������� ó���ϴ� ����� �����ϸ� call�� ������ ����. 
*  call�� �Ϲ����� �Լ��� ���������� �Ű������� ���� ������, apply�� �Ű������� �迭�� �޴´�.
```js
    update.apply(bruce, [1955, 'actor']);
    /*
        bruce�� ����
        {
            name : 'Bruce',
            birthYear : 1955,
            occupation : 'actor'
        }
        �� �����
     */

    update.apply(madeline, [1918, 'writer']);
    /*
        madeline�� ����
        {
            name : 'Madeline',
            birthYear : 1918,
            occupation : 'writer'
        }
        �� �����
     */
```
*  apply�� �迭 ��Ҹ� �Լ� �Ű������� ����ؾ� �� �� �����ϴ�. 
*  �ڹٽ�ũ��Ʈ�� ���� �Լ��� Math.min�� Math.max�� �Ű������� �޾� ���� �ּҰ��� �ִ밪�� ���� ��ȯ�Ѵ�.
*  apply�� ����ϸ� ���� �迭�� �̵� �Լ��� �ٷ� �ѱ� �� �ִ�.
```js
    const arr = [2,3,-5,15,7];

    Math.min.apply(null, arr); // -5
    Math.max.apply(null, arr); // 15
```
### bind
*  bind�� ����ϸ� �Լ��� this ���� ������ �ٲ� �� �ִ�. 
*  update �޼��带 �̸����� �ű�鼭 ȣ���� �� this ���� �׻� bruce�� �ǰԲ�, call�̳� apply, �ٸ� bind�� �Բ� ȣ���ϴ��� this ���� bruce�� �ǵ��� �Ϸ��� bind�� ����Ѵ�.
```js
    const updateBruce = update.bind(bruce);

    updateBruce(1904, "actor");
    // bruce �� ���� { name: "Bruce", birthYear: 1904, occupation: "actor" }

    updateBruce.call(madeline, 1274, "king");
    // bruce �� ���� { name: "Bruce", birthYear: 1274, occupation: "king" };
    // madeline�� ������ ����
```

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
### Prototype
![prototype_function](./img/prototype_function.jpg)
*  �Լ��� �����ϸ� ���� ���� function, prototype 2���� ��ü�� �����ȴ�.
*  �� �� ��ü�� ���� ���� ������ property�� ������ �ִ�.
  *  function�� prototype�� ���� prototype ��ü�� �����Ѵ�.
  *  prototype�� constructor�� ���� function ��ü�� �����Ѵ�.
*  ���� �Ӹ��� �ƴ϶� ���浵 �����ϴ�.
*  function �����δ� prototype�� property�� ������ �� ����.
```js
function Foo (){}
Foo.prototype.proto_val = '���� ��';

Foo.prototype.constructor.construct_val = "������ ��";

console.log(Foo.prototype.proto_val); //���� �� �� ���
console.log(Foo.construct_val); //������ �� �� ���
console.log(Foo.proto_val); //?! undefined�� ���
```

![prototype_function_instance](./img/prototype_function_instance.jpg)
*  instanceȭ �Ǹ� prototype�� property�� ���� �� �� �ִ� ������ �����ȴ�.
```js
function Foo (){} //�Լ� ����
Foo.prototype.proto_val = "���� �� ���ִ�!!"; //Foo�� ������Ÿ���� ����

var foo_instance = new Foo();  //Foo�� �ν��Ͻ��� ����

console.log(foo_instance.proto_val); //���� �� ���ִ�!! �� ���
```
*  instance ���� property�� �����ص� ```__proto__``` ���� property�� ������ �ʴ´�.
```js
function Foo(){}

Foo.prototype.proto_val = 100;    //������Ÿ�� �Ӽ��� �����մϴ�.

var foo_instance = new Foo();  //Foo�� �ν��Ͻ��� �����մϴ�.

console.log(foo_instance.proto_val); //������Ÿ�԰� 100�� ����� �մϴ�.

foo_instance.proto_val -= 1;  // �ν��Ͻ����� proto_val�� 1�ٿ����ϴ�.

console.log(foo_instance.__proto__.proto_val); //������Ÿ���� ���� �״���Դϴ�.
console.log(foo_instance.proto_val);  //������ �ν��Ͻ��� 1�� ���� 99�� ����� �˴ϴ�.
```

### Prototype Inheritance
![prototype_inheritance](./img/prototype_inheritance.jpg)
*  �Լ��� �����ϴ� ���� Object.prototype�� ����ϰ� �ȴ�.
*  prototype chain�� prototype�� �ٸ� prototype�� �����ϴ� ������ �ݺ��Ǵ� ���̴�.
```js
Object.prototype.say = function(){
    console.log(this.greet); //Object�� ������Ÿ�Կ� say��� �޼��带 �߰��մϴ�.
}

function Foo (){
    this.greet = "hello world";    // Foo �����ڿ��� greet�̶�� �Ӽ��� �߰��մϴ�.
}

var foo_instance = new Foo();     //�ν��Ͻ��� �����մϴ�.

foo_instance.say(); //hello world�� ����մϴ�.
```
1. instance ���� say�� �ִ��� Ȯ���Ѵ�.  
2. ���ٸ� instance�� �����ϴ� prototype�� say�� �ִ��� Ȯ���Ѵ�.  
3. ���ٸ� prototype�� �����ϴ� prototype�� say�� �ִ��� Ȯ���Ѵ�.  
4. �� ������ �ݺ��ϴٰ� null�� ������ �ߴ��ϰ� say�� undefined�� �Ҵ��Ѵ�.  
5. say�� ã�� ��� say�� ȣ���Ѵ�.  

*  �ٸ� ��ü������ ���
```js
function Vehicle (){}

Vehicle.prototype.wheels = 4;
Vehicle.prototype.getWheels = function(){ //Vehicle�� ������Ÿ���� �Ӽ��� �����մϴ�.
    console.log(this.wheels);
}

function Bicycle(){
    this.wheels = 2;
}

Bicycle.prototype.__proto__ = Vehicle.prototype; //Bicycle�� ������Ÿ����  Vehicle�� ������Ÿ���� �����ϰ� �մϴ�.

var bicycle = new Bicycle(); //��ü�� �����մϴ�. 

bicycle.getWheels();  // 2�� ����մϴ�.
```
![object_vehicle_bicycle](./img/object_vehicle_bicycle.jpg)
1. getWheels method�� ������ ��� instance bicycle �ȿ� �ش� method�� ���� ������ prototype Bicycle�� �����ϴ� Vehicle�� Ȯ���Ѵ�.  
2. prototype Vehicle �ȿ��� getWheels method�� �ֱ� ������ ȣ���Ѵ�.  

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
### map
map() �޼���� �迭 ���� ��� ��� ������ ���Ͽ� ������ �Լ�(callback)�� ȣ���ϰ� �� ����� ��Ƽ� ���ο� �迭�� ��ȯ�Ѵ�.
```js
var num = [2, 4, 6, 8];
var result = num.map(function(num) { return num * 10; });
console.log(result); // [20, 40, 60, 80]
```

### reduce
reduce() �޼���� ���ʿ��� ���������� �̵��ϸ� �迭�� �� ��Ҹ��� ���� ��갪�� �Բ� �Լ��� ������ �ϳ��� ������ ���δ�.
```js
var sumArr = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10];
var result = sumArr.reduce(function(prev, curr) { return prev + curr; });
console.log(result); // 55
```

### filter
filter() �޼���� ������ �Լ��� ������ �׽�Ʈ�� ��ȭ�ϴ� ��� ��Ұ� �ִ� ���ο� �迭�� �����.
```js
var persons = [
  { name: "aaa", learn: "javascript" },
  { name: "bbb", learn: "javascript" },
  { name: "ccc", learn: "java" },
  { name: "ddd", learn: "javascript" }
];

var isJava = function(person) {
  return person.learn === 'java';
};

var result = persons.filter(isJava);

console.log(result); // { name: 'ccc', learn: 'java' }
```

### some
some() �޼���� �迭 �� �Ϻ� ��Ұ� ������ �Լ��� ���� ������ �׽�Ʈ�� ����ϴ� ���� �׽�Ʈ�Ѵ�.
```js
var aTeam = [
  { id: 1, name: "Steven", xMan: false },
  { id: 2, name: "Steve", xMan: false },
  { id: 3, name: "James", xMan: false }
];

var bTeam = [
  { id: 1, name: "Dennis", xMan: false },
  { id: 2, name: "Linus", xMan: false },
  { id: 3, name: "Rocket Man", xMan: true }
];

var isXman = function(arr) { return arr.xMan; };

console.log(aTeam.some(isXman)); // false
console.log(bTeam.some(isXman)); // true
```

### ������ ����
1. �迭���� �ߺ� �����ϱ�
```js
let values = [3, 1, 3, 5, 2, 4, 4, 4];
let uniqueValues = [...new Set(values)];
// uniqueValues is [3, 1, 5, 2, 4]
```
2. ������ �˻�(case-sensitive)
```js
let users = [
  { id: 11, name: 'Adam', age: 23, group: 'editor' },
  { id: 47, name: 'John', age: 28, group: 'admin' },
  { id: 85, name: 'William', age: 34, group: 'editor' },
  { id: 97, name: 'Oliver', age: 28, group: 'admin' }
];
let res = users.filter(it => it.name.includes('oli'));
// res is []
```
3. ������ �˻�(case-insensitive)
```js
let res = users.filter(it => new RegExp('oli', "i").test(it.name));
// res is
[
  { id: 97, name: 'Oliver', age: 28, group: 'admin' }
]
```
4. Ư�� ������ admin ������ ���� �ִ��� Ȯ��
```js
let hasAdmin = users.some(user => user.group === 'admin');
// hasAdmin is true
```
5. array of arrays ��ġ��
```js
let nested = [[1, 2, 3], [4, 5, 6], [7, 8, 9]];
let flat = nested.reduce((acc, it) => [...acc, ...it], []);
// flat is [1, 2, 3, 4, 5, 6, 7, 8, 9]
```
6. Ư�� Ű�� �󵵸� �����ϴ� ��ü�� �����
```js
let users = [
  { id: 11, name: 'Adam', age: 23, group: 'editor' },
  { id: 47, name: 'John', age: 28, group: 'admin' },
  { id: 85, name: 'William', age: 34, group: 'editor' },
  { id: 97, name: 'Oliver', age: 28, group: 'admin' }
];
let groupByAge = users.reduce((acc, it) =>
  ({ ...acc, [it.age]: (acc[it.age] || 0) + 1 }),
{});
// groupByAge is {23: 1, 28: 2, 34: 1}
```
7. array of objects �ε��� (lookup table)
```js
let uTable = users.reduce((acc, it) => ({...acc, [it.id]: it }), {})
// uTable equals:
{
  11: { id: 11, name: 'Adam', age: 23, group: 'editor' },
  47: { id: 47, name: 'John', age: 28, group: 'admin' },
  85: { id: 85, name: 'William', age: 34, group: 'editor' },
  97: { id: 97, name: 'Oliver', age: 28, group: 'admin' }
}
```
8. �迭 ���� ������ item���� Ư�� Ű�� ������ ���� �̾Ƴ���
```js
let listOfUserGroups = [...new Set(users.map(it => it.group))];
// listOfUserGroups is ['editor', 'admin'];
```
9. ��ü key-value map ����
```js
let cities = {
  Lyon: 'France',
  Berlin: 'Germany',
  Paris: 'France'
};

let countries = Object.keys(cities).reduce((acc, k) => {
  let country = cities[k];
  acc[country] = [...(acc[country] || []), k];
  return acc;
}, {});

// countries is
{
  France: ["Lyon", "Paris"],
  Germany: ["Berlin"]
}
```
10. ���� �µ��� ȭ�� �µ��� �ٲٱ�
```js
let celsius = [-15, -5, 0, 10, 16, 20, 24, 32]
let fahrenheit = celsius.map(t => t * 1.8 + 32);
// fahrenheit is [5, 23, 32, 50, 60.8, 68, 75.2, 89.6]
```
11. ��ü�� ���� ��Ʈ������ ���ڵ��ϱ�
```js
let params = {lat: 45, lng: 6, alt: 1000};
let queryString = Object.entries(params).map(p => encodeURIComponent(p[0]) + '=' + encodeURIComponent(p[1])).join('&')
// queryString is "lat=45&lng=6&alt=1000"
```
12. ��õ� Ű�� �Բ� �б� ������ string ���� ���� ���̺� ���
```js
let users = [
  { id: 11, name: 'Adam', age: 23, group: 'editor' },
  { id: 47, name: 'John', age: 28, group: 'admin' },
  { id: 85, name: 'William', age: 34, group: 'editor' },
  { id: 97, name: 'Oliver', age: 28, group: 'admin' }
];
users.map(({id, age, group}) => `\n${id} ${age} ${group}`).join('')
// it returns:
"
11 23 editor
47 28 admin
85 34 editor
97 28 admin"
```
13. ��ü �迭���� key-value ���� ã�Ƽ� �ٲٱ�
```js
let updatedUsers = users.map(
  p => p.id !== 47 ? p : {...p, age: p.age + 1}
);
// John is turning 29 now
```
14. A�� B�� ������
```js
let arrA = [1, 4, 3, 2];
let arrB = [5, 2, 6, 7, 1];
[...new Set([...arrA, ...arrB])]; // returns [1, 4, 3, 2, 5, 6, 7]
```
15. A�� B�� ������
```js
let arrA = [1, 4, 3, 2];
let arrB = [5, 2, 6, 7, 1];
arrA.filter(it => arrB.includes(it)); // returns [1, 2]
```
**[? ����](#����)**

---

## Pure Functions, Side Effects and State Mutation
*  Pure Function(���� �Լ�)�� ���������̴�.
���� �Է¿��� �׻� ���� ����� �����Ѵ�.
```js
const add = (x, y) => x + y // A pure function
```
```js
const magicLetter = '*'
const createMagicPhrase = (phrase) => `${magicLetter}abra${phrase}` // An impure function
```
```js
const fetchLoginToken = externalAPI.getUserToken // An impure function
```
*  Side Effect�� �Լ� �ܺ� �ý����� �����̴�.
*  ���� �Լ��� side effect�� ����.
  *  �Լ��� �ܺ� ���¸� �����ϰų� �Լ��� ���� ������ ���¸� �������� �ʴ´�.  
  *  �Լ��� ����� ����� ���� ���ؼ� ���ڿ��� �����Ѵ�.
*  Mutation�� �迭�̳� object ���� source element�� �����ϰų� ������ �ִ� ���� �ǹ��Ѵ�.
*  ���α׷����� ��ȭ�� �ִ� ���� �������� �����ؾ� �� �κ��� �������Ƿ� ���α׷��� �� ������ ����.  
*  ����� �Լ�
```js
const cities = ['����']

function addElement(array, element) {
  const newArray = array
  newArray.push(element)
  return newArray
}

const newCities = addElement(cities, '�λ�')
console.log(newCities) // [ '����', '�λ�' ]
console.log(cities) // [ '����', '�λ�' ]

const newCities2 = addElement(cities, '�λ�')
console.log(newCities2) // [ '����', '�λ�', '�λ�' ]
console.log(cities) // [ '����', '�λ�', '�λ�' ]
```
*  ���� �Լ��� ����
```js
function addElement(array, element) {
  const newArray = [...array]
  newArray.push(element)
  return newArray
}
```
**[? ����](#����)**

---

## Closures
*  Ŭ������ �������� ���� ������ ����Ű�� �Լ��̴�.
*  Ŭ���� �ȿ��� ���ǵ� �Լ��� ������� ȯ���� ����Ѵ�.
### ����
```js
function getClosure() { 
  var text = 'variable 1';
  return function() { return text; };
} 

var closure = getClosure(); 
console.log(closure()); // 'variable 1'
```
*  getClosure()�� �Լ��� ��ȯ�ϰ�, ��ȯ�� �Լ��� getClosure() ���ο� ����� ������ �����ϰ� �ִ�.
*  �̷��� ������ ������ �Լ� ������ ������ ������� �ʰ� ���� ��ȯ�Ѵ�.
*  getClosure()�� ��ȯ�� closure �Լ��� Ŭ�����̴�.
*  Ŭ������ ����� ��� �ܺο��� Ŭ���� �Լ� ������ ������ ������ ����� ���� ������ `Capsulation(����ȭ)` �ȴ�.
*  Ŭ������ ���� ������ �����ϴ� ���ȿ��� ���� ������ Garbage Collection ����� �ƴϱ� ������ �޸𸮰� ȸ������ �ʴ´�. ���� Ŭ���� ����� ������ ������ �����ϴ� ���� ����.

**[? ����](#����)**

---

## High Order Functions
*  High Order Function(���� �Լ�)�� �Լ��� ���ڷ� ���� �ްų� �Լ��� ����� ��ȯ�ϴ� �Լ��� ���Ѵ�.
*  ���� �Լ��� �ܺ� ���� �����̳� ����(mutable) �����͸� ���ϰ� �Һ���(Immutability)�� �����ϴ� �Լ��� ���α׷��ֿ� ����� �ΰ� �ִ�.
```js
// �Լ��� ���ڷ� ���޹ް� �Լ��� ��ȯ�ϴ� ���� �Լ�
function makeCounter(predicate) {
  // ���� ����. num�� ���´� �����Ǿ�� �Ѵ�.
  let num = 0;
  // Ŭ����. num�� ���¸� �����Ѵ�.
  return function () {
    // predicate�� ���� ���� num�� ���¸� ��ȭ��Ų��.
    num = predicate(num);
    return num;
  };
}

// ���� �Լ�
function increase(n) {
  return ++n;
}

// ���� �Լ�
function decrease(n) {
  return --n;
}

// makeCounter�� �Լ��� �μ��� ���޹޴´�. �׸��� Ŭ������ ��ȯ�Ѵ�.
const increaser = makeCounter(increase);
console.log(increaser()); // 1
console.log(increaser()); // 2

// makeCounter�� �Լ��� �μ��� ���޹޴´�. �׸��� Ŭ������ ��ȯ�Ѵ�.
const decreaser = makeCounter(decrease);
console.log(decreaser()); // -1
console.log(decreaser()); // -2
```
**[? ����](#����)**

---

## Recursion
...
**[? ����](#����)**

---

## Collections and Generators
### Colections
*  �ڹٽ�ũ��Ʈ���� ������ ���� ������ �÷����� �ִ�.
  *  Indexed Collection : Arrays, Typed Array
  *  Keyed Collection : Objects, Map, Set, Weak Map, Weak Set
*  ES6���� �߰��� �÷��� : Typed Array, Map, Set, Weak Map, Weak Set
#### Set
*  Set�� value�� key������ ���� �÷����̴�.
*  Set�� ���� �߰�, ���� �� ������ �����ϴ�.
*  Set�� ���� �ߺ����� �ʴ´�.
##### Set �޼��� ��뿹  
*  size : ũ��
*  has : �� Ȯ��
*  add : �� �߰�
*  delete : �� ����
*  forEach : �ݺ���
*  clear : ��� �� ����
```js
let animals = new Set();

animals.add('??');
animals.add('??');
animals.add('??');
animals.add('??');
console.log(animals.size); // 4
animals.add('??');
console.log(animals.size); // 4

console.log(animals.has('??')); // true
animals.delete('??');
console.log(animals.has('??')); // false

animals.forEach(animal => {
  console.log(`Hey ${animal}!`);
});

// Hey ??!
// Hey ??!
// Hey ??!

animals.clear();
console.log(animals.size); // 0
```
##### array�� ����� Set �ʱ�ȭ
```js
let myAnimals = new Set(['??', '??', '??', '??']);

myAnimals.add(['??', '??']);
myAnimals.add({ name: 'Rud', type: '??' });
console.log(myAnimals.size); // 4

myAnimals.forEach(animal => {
  console.log(animal);
});


// ??
// ??
// ["??", "??"]
// Object { name: "Rud", type: "??" }
```
##### string�� ����� Set �ʱ�ȭ
```js
console.log('Only unique characters will be in this set.'.length); // 43

let sentence = new Set('Only unique characters will be in this set.');
console.log(sentence.size); // 18
```
##### for...of�� ����� loop
```js
let moreAnimals = new Set(['??', '??', '??', '??']);

for (let animal of moreAnimals) {
  console.log(`Howdy ${ animal }`);
}

// Howdy ??
// Howdy ??
// Howdy ??
// Howdy ??
```
##### keys�� values �޼���(������ ���)
```js
let partyItems = new Set(['??', '??', '??']);
let items = partyItems.values();

console.log(items.next());
console.log(items.next());
console.log(items.next());
console.log(items.next().done);

// Object {
//   done: false,
//   value: "??"
// }

// Object {
//   done: false,
//   value: "??"
// }

// Object {
//   done: false,
//   value: "??"
// }

// true
```
**[? ����](#����)**
#### Map
*  Map�� Key - Value ������ �̷���� �÷����̴�.
*  Map�� object�� �ٸ��� ��� Ÿ���� key�� ����� �� �ִ�(object�� function������...)
##### Map �޼��� ��뿹  
*  size : ũ��
*  has : �� Ȯ��
*  set : �� �߰�
*  get : �� ��������
*  delete : �� ����
*  clear : ��� �� ����
```js
let things = new Map();

const myFunc = () => '??';

things.set('??', 'Car');
things.set('??', 'House');
things.set('??', 'Airplane');
things.set(myFunc, '?? Key is a function!');

things.size; // 4

things.has('??'); // true

things.has(myFunc) // true
things.has(() => '??'); // false, not the same reference
things.get(myFunc); // '?? Key is a function!'

things.delete('??');
things.has('??'); // false

things.clear();
things.size; // 0

// setting key-value pairs is chainable
things.set('??', 'Wrench')
      .set('??', 'Guitar')
      .set('??', 'Joystick');

const myMap = new Map();

// Even another map can be a key
things.set(myMap, 'Oh gosh!');
things.size; // 4
things.get(myMap); // 'Oh gosh!'
```
##### Map�� array�� �ʱ�ȭ
```js
const funArray = [
  ['??', 'Champagne'],
  ['??', 'Lollipop'],
  ['??', 'Confetti'],
];

let funMap = new Map(funArray);
funMap.get('??'); // Champagne
```
##### Map �ݺ��� 
*  for...of�� array destructuring�� ����
```js
let activities = new Map();

activities.set(1, '??');
activities.set(2, '??');
activities.set(3, '??');
activities.set(4, '??');

for (let [nb, activity] of activities) {
  console.log(`Activity ${nb} is ${activity}`);
}

// Activity 1 is ??
// Activity 2 is ??
// Activity 3 is ??
// Activity 4 is ??
```
*  forEach�� ����
```js
activities.forEach((value, key) => {
  console.log(`Activity ${key} is ${value}`);
});
```
#### WeakSet, WeakMap
*  �ڹٽ�ũ��Ʈ�� garbage collection�� �� �̻� �������� �ʴ� object�� �ڵ����� �����ǰ� �� resource�� ��ã�� �޸� ���� �����̴�.
*  Map�� Set�� object ������ ���ϰ� ���յǾ� �־� garbage collection�� ������� �ʴ´�.
*  WeakSet�� WeakMap�� �� �̻� �ʿ����� �ʴ� object�� �޸𸮿��� ���� �� �ִ�.
*  Weak �÷����� �Ϲ� �÷��ǰ� ������ ��������� ��� ������ �޼��� ���� ����.
*  WeakSet ��뿹
```js
const yesdoing = new WeakSet(); // WeakMap�� �����մϴ�. 
const age = {}; // ���� �ݵ�� ��ü���� �մϴ�. 

yesdoing.add(age); // ���� �߰��մϴ�.

yesdoing.has(age); // True
yesdoing.delete(age) // ���� �����մϴ�.
```
*  WeakMap ��뿹
```js
const yesdoing = new WeakMap(); // WeakMap�� �����մϴ�. 
const age = {}; // Ű�� �ݵ�� ��ü���� �մϴ�.
const job = {}; // Ű�� �ݵ�� ��ü���� �մϴ�.

yesdoing.set(age, 11111); // Ű - ���� �����մϴ�.
yesdoing.set(job, 'air'); // �����δ� � Ÿ���̶� ���� �� �ֽ��ϴ�. 

yesdoing.has(job); // True
yesdoing.delete(job) // key�� �����մϴ�.
```
### Generator
*  Generator�� ES6���� �����Ǵ� ����̴�.
*  Generator�� ```(*)``` Ű���带 ����Ͽ� ������ �� �ִ�.
*  �Ϲ� �Լ��� �� ���ึ�� ���� �帧���� �ڵ带 ���������� Generator�� ���� �߿� �ߴ� �� �� ��ȯ�� �ߴٰ� �ٽ� �ߴ� �������� ������ �� �ִ�.
![generator_vs_function](./img/generator_vs_function.PNG)
#### yield�� next()
```js
function* gen() {
    console.log("ù next");
    yield 1;
    console.log("�ι� ° next");
    yield 2;
    console.log("���� ° next");
    yield 3;
    console.log("�׹� ° next");
}

var g = gen(); // ���ʷ����� ��ü ��ȯ

console.log(g.next()); // {value: 1, done: false}
console.log(g.next()); // {value: 2, done: false}
console.log(g.next()); // {value: 3, done: false}
console.log(g.next()); // {value: undefined, done: true}
```
```js
ù next
{value: 1, done: false}
�ι� ° next
{value: 2, done: false}
���� ° next
{value: 3, done: false}
�׹� ° next
{value: undefined, done: true}
```
#### next(parameter)
```js
function* gen() {
    var bar = yield 'foo';
    console.log(bar); // bar
}

var g = gen();

console.log(g.next()); // {value: 'foo', done: false}
console.log(g.next('bar'));
```
```js
{value: "foo", done: false}
bar
{value: undefined, done: true}
```
#### yield *
```js
function* gen1() {
    yield 1;
    yield 2;
}

function* gen2() {
    // yield* ��  gen1 �� �����Ѵ�.
    yield* gen1();
    yield 3;
}

var g = gen2();

console.log(g.next()); // {value: 1, done: false}
console.log(g.next()); // {value: 2, done: false}
console.log(g.next()); // {value: 3, done: false}
console.log(g.next()); // {value: undefined, done: true}
```
#### return()�� throw()
```js
function* gen() {
    yield 1;
    yield 2;
    yield 3;
}

var g = gen();

console.log(g.next()); // {value: 1, done: false}
console.log(g.return(123)); // {value: 123, done: true}

var g2 = gen();
console.log(g2.next()); // {value: 1, done: false}
console.log(g2.throw("error ȣ��")); // ���� ȣ��, ���ʷ����� ����
```
#### Generator ��� ����
*  Lazy Evaluation(������ ����)
    *  ����� ������� �ʿ��� ������ ����� ���ߴ� ���
    *  ���� �ʿ����� ������ �������� �ʰ�, ��û�� ���ȴ�.
```js
// �Ϲ����� ����� �ڵ�
let arr = [];
for (let i = 0; i < 100; i++) {
    arr.push(i);
}
```
```js
// Generator�� ������ �ڵ�
function* arr() {
    let i = 0;
    while (i < 100) {
        yield i++;
    }
}
console.log([...arr()]);
```
*  �񵿱� ���α׷����� ���������� �ۼ��ϰ� �����ϱ� ���ؼ�
*  Infinite iterator
```js
function* idMaker() {
    var index = 0;
    while(true)
        yield index++;
}

var gen = idMaker(); // "Generator { }"

console.log(gen.next().value); // 0
console.log(gen.next().value); // 1
console.log(gen.next().value); // 2
// ...
```
---

## Promises
*  ���ι̽��� �ڹٽ�ũ��Ʈ �񵿱� ó���� ���Ǵ� ��ü�̴�.
*  �ڹٽ�ũ��Ʈ�� �񵿱� ó���� 'Ư�� �ڵ��� ������ �Ϸ�� ������ ��ٸ��� �ʰ� ���� �ڵ带 ���� �����ϴ� �ڹٽ�ũ��Ʈ�� Ư��'�� �ǹ��Ѵ�.
*  �ַ� �������� �޾ƿ� �����͸� ȭ�鿡 ǥ���� �� ����Ѵ�.
### ����
*  ���ι̽� ���� ��(callback ���)
```js
function getData(callbackFunc) {
  $.get('url �ּ�/products/1', function (response) {
    callbackFunc(response); // �������� ���� ������ response�� callbackFunc() �Լ��� �Ѱ���
  });
}

getData(function (tableData) {
  console.log(tableData); // $.get()�� response ���� tableData�� ���޵�
});
```
*  ���ι̽� ����
```js
function getData(callback) {
  // new Promise() �߰�
  return new Promise(function (resolve, reject) {
    $.get('url �ּ�/products/1', function (response) {
      // �����͸� ������ resolve() ȣ��
      resolve(response);
    });
  });
}

// getData()�� ������ ������ ȣ��Ǵ� then()
getData().then(function (tableData) {
  // resolve()�� ��� ���� ����� ���޵�
  console.log(tableData); // $.get()�� reponse ���� tableData�� ���޵�
});
```
### Promise ������ ����
#### Pending(���)
*  �񵿱� ó�� ������ ���� �Ϸ���� ���� ����
*  �Ʒ��� ���� `new Promise()`�� ȣ���ϸ� Pending(���) ���°� �ȴ�.
```js
new Promise();
```
*  ������ ���� `new Promise()`�� ȣ���� �� �ݹ� �Լ��� ���ڷ� resolve, reject�� ������ �� �ִ�.
```js
new Promise(function (resolve, reject) {
  // ...
});
```
#### Fulfilled(����)
*  �񵿱� ó���� �Ϸ�Ǿ� ���ι̽��� ��� ���� ��ȯ���� ����
*  �ݹ� �Լ��� ���� resolve�� �Ʒ��� ���� �����ϸ� Fulfilled(����) ���°� �ȴ�.
```js
new Promise(function (resolve, reject) {
  resolve();
});
```
*  ���� ���°� �Ǹ� �Ʒ��� ���� `then()`�� �̿��Ͽ� ó�� ��� ���� ���� �� �ִ�.
```js
function getData() {
  return new Promise(function (resolve, reject) {
    var data = 100;
    resolve(data);
  });
}

// resolve()�� ��� �� data�� resolvedData�� ����
getData().then(function (resolvedData) {
  console.log(resolvedData); // 100
});
```
#### Rejected(����)
*  �񵿱� ó���� �����ϰų� ������ �߻��� ����
*  reject ���ڷ� reject() �޼��带 �����ϸ� Rejected(����) ���°� �ȴ�.
```js
new Promise(function (resolve, reject) {
  reject();
});
```
*  ���� ���°� �Ǹ� ������ ����(���� ó���� ��� ��)�� `catch()`�� ���� �� �ֽ��ϴ�.
```js
function getData() {
  return new Promise(function (resolve, reject) {
    reject(new Error("Request is failed"));
  });
}

// reject()�� ��� �� Error�� err�� ����
getData().then().catch(function (err) {
  console.log(err); // Error: Request is failed
});
```
#### ���ι̽� ���� 2
```js
function getData() {
  return new Promise(function (resolve, reject) {
    $.get('url �ּ�/products/1', function (response) {
      if (response) {
        resolve(response);
      }
      reject(new Error("Request is failed"));
    });
  });
}

// Fulfilled �Ǵ� Rejected�� ��� �� ���
getData().then(function (data) {
  console.log(data); // response �� ���
}).catch(function (err) {
  console.error(err); // Error ���
});
```
#### ���ι̽� ����(Promise Chaining)
```js
new Promise(function(resolve, reject){
  setTimeout(function() {
    resolve(1);
  }, 2000);
})
.then(function(result) {
  console.log(result); // 1
  return result + 10;
})
.then(function(result) {
  console.log(result); // 11
  return result + 20;
})
.then(function(result) {
  console.log(result); // 31
});
```
#### ���ι̽� ���� 3
```js
getData(userInfo)
  .then(parseValue)
  .then(auth)
  .then(diaplay);
```
```js
var userInfo = {
  id: 'test@abc.com',
  pw: '****'
};

function parseValue() {
  return new Promise({
    // ...
  });
}
function auth() {
  return new Promise({
    // ...
  });
}
function display() {
  return new Promise({
    // ...
  });
}
```
#### ���ι̽� ���� ó��
```js
function getData() {
  return new Promise(function (resolve, reject) {
    reject('failed');
  });
}

// 1. then()���� ������ ó���ϴ� �ڵ�
getData().then(function () {
  // ...
}, function (err) {
  console.log(err);
});

// 2. catch()�� ������ ó���ϴ� �ڵ� (�����ϴ� ���)
getData().then().catch(function (err) {
  console.log(err);
});
```
**[? ����](#����)**

---

## async/await
*  Promise ������ �ذ��ϱ� ���� ES7(ES2017)���� async/await Ű���尡 �߰��Ǿ���.
*  async/await Ű���带 ����ϸ� �񵿱� �ڵ带 ��ġ ���� �ڵ�ó�� __���̰�__ �ۼ��� �� �ִ�.
### async/await ����
```js
// Promise�� ����� �ڵ�
function fetchAuthorName(postId) {
  return fetch(`https://jsonplaceholder.typicode.com/posts/${postId}`)
    .then(response => response.json())
    .then(post => post.userId)
    .then(userId => {
      return fetch(`https://jsonplaceholder.typicode.com/users/${userId}`)
        .then(response => response.json())
        .then(user => user.name);
    });
}

fetchAuthorName(1).then(name => console.log("name:", name));
```
```js
// async/await�� ����� �ڵ�
async function fetchAuthorName(postId) {
  const postResponse = await fetch(`https://jsonplaceholder.typicode.com/posts/${postId}`);
  const post = await postResponse.json();
  const userId = post.userId;
  const userResponse = await fetch(`https://jsonplaceholder.typicode.com/users/${userId}`)
  const user = await userResponse.json();
  return user.name;
}

fetchAuthorName(1).then(name => console.log("name:", name));
```
*  async Ű���带 function �տ� ���δ�.
*  Promise�� �����ϴ� ��� �񵿱� �Լ� ȣ��� �տ��� await Ű���带 �߰��Ѵ�.
*  await Ű����� async Ű���尡 �پ��ִ� �Լ� ���ο����� ��� �����ϴ�.
*  async Ű���尡 �پ� �ִ� �Լ��� ȣ���ϸ� ��������� Promise ��ü�� �����Ͽ� �������� �ʾƵ� Promise ��ü�� ���ϵȴ�.
### async/await ���� ó��
```js
async function fetchAuthorName(postId) {
    const postResponse = await fetch(`https://jsonplaceholder.typicode.com/posts/${postId}`);
    const post = await postResponse.json();
    const userId = post.userId;
    
    try {
        const userResponse = await fetch(`https://jsonplaceholder.typicode.com/users/${userId}`)
        const user = await userResponse.json();
        return user.name;
    } catch (err) {
        console.log('Faile to fetch user:', err);
        return "Unknown";
    }
}

fetchAuthorName(1).then(name => console.log("name:", name));
```
**[? ����](#����)**
---

## Data Structures
...
**[? ����](#����)**

---

## Expensive Operation and Big O Notation
### Expensive Operation
####  Looping Over an Array
1������ ���� ���� ���ϴ� ���� ���
*  For Loop, average loop time: ~10 microseconds
*  For-Of, average loop time: ~110 microseconds
*  ForEach, average loop time: ~77 microseconds
*  While, average loop time: ~11 microseconds
*  Reduce, average loop time: ~113 microseconds
#### Duplicating an Array
1������ ��Ҹ� ���� 1������ array�� �����ϴ� ���� ���
*  Duplicate using Slice(`arr.slice()`), average: ~367 microseconds
*  Duplicate using Map(`arr.map(x =>x)`, ES5), average: ~469 microseconds
*  Duplicate using Spread(`[��arr]`, ES6), average: ~512 microseconds
*  Duplicate using Concat(`[].concat(arr)`), average: ~366 microseconds
*  Duplicate using Array From(`Array.from(arr)`), average: ~1,436 microseconds
*  Duplicate manually, average: ~412 microseconds
#### Iterating Objects
���� 1õ���� ���� key�� value�� ���� 1������ object�� iteration�ϴ� ���� ���
*  Object iterate For-In(`for(let key in obj)`), average: ~240 microseconds
*  Object iterate Keys For Each(`Object.keys(obj)`, ES6), average: ~294 microseconds
*  Object iterate Entries For-Of(`Object.entries(obj)`, ES8), average: ~535 microseconds

### Big O Notation
*  big-O�� �˰����� ȿ������ ��Ÿ���� ��ǥ�̴�.
*  big-O ǥ����� ���� �˰����� �ð� ���⵵�� ���� ���⵵�� ��Ÿ���µ� �ַ� ���ȴ�.
*  Big-O ǥ����� ������ �Է°�(n)�� ũ�⿡ ���� ������ �޴´�.
#### O(1) - Constant Time Complexity
*  �Է°�(n)�� ũ��� ������� �׻� ������ �ð� ������ ���̴� ���� `O(1)`�̶�� ǥ���Ѵ�.
*  JavaScript �Լ��� ���� �ֻ��� �ó������� ���ֵȴ�.  
![big_o_o(1)](./img/big_o_o(1).PNG)
#### O(n) - Linear
*  �Է°�(n)�� ũ�⿡ ���� �ð� ������ �����ϰ� �þ�� ���� `O(n)`�̶�� ǥ���Ѵ�.
*  �迭�� ������ �μ��Ѵٰ� �������� �� �鸸���� ��Ҹ� �����ϸ� �鸸���� �ݺ��� �ʿ��ϴ�.  
![big_o_o(n)](./img/big_o_o(n).PNG)
#### O(log n) ? Logarithmic
*  �Է°�(n)�� ũ�⿡ ���� ���� �ð��� ���������� ���� �ð��� �����Ǵ� �ӵ��� �����ϴ� ������ ���̴� ���� `O(log n)`�̶�� ǥ���Ѵ�.
*  ���� Ʈ�� Ž���� ���� �� �� �ִ�.  
![big_o_o(logn)](./img/big_o_o(logn).PNG)
#### O(n^2) ? Quadratic
*  �Է°�(n)�� ũ�⿡ ���� ���� �ð��� �����ϴ� �ӵ��� ���� �ް��� �����ϴ� ������ ���̴� ���� `O(n^2)`�̶�� ǥ���Ѵ�.
*  2�� for ���� ����ϸ鼭 ������ �Ǿ����� ���� ��ҵ��� �ϳ��ϳ� Ž���ϴ� ����� ���� �� �� �ִ�.  
![big_o_o(n^2)](./img/big_o_o(n^2).PNG)  

**[? ����](#����)**

---

## Algorithms
...
**[? ����](#����)**

---

## Inheritance, Polymorphism and Code Reuse
### Inheritance (Class-Style)
ES6������ C++�� Java�� ������ Ŭ���� ������ �����Ͽ� Ŭ������ �� ���� ��Ȯ�ϰ� ��Ȱ�� �� �� �ְ� �Ǿ���.
```js
class Person {
  constructor(first, last, age, gender, interests) {
    this.name = {
      first,
      last
    };
    this.age = age;
    this.gender = gender;
    this.interests = interests;
  }

  greeting() {
    console.log(`Hi! I'm ${this.name.first}`);
  };

  farewell() {
    console.log(`${this.name.first} has left the building. Bye for now!`);
  };
}
```
```js
class Teacher extends Person {
  constructor(first, last, age, gender, interests, subject, grade) {
    super(first, last, age, gender, interests);
    // subject and grade are specific to Teacher
    this._subject = subject;
    this.grade = grade;
  }

  get subject() {
    return this._subject;
  }

  set subject(newSubject) {
    this._subject = newSubject;
  }
}
```
### Polymorphism
*  �������� Ư�� ����� ����(����) �κа� ����(����) �κ����� �и������ν� �ϳ��� �ൿ�� ���� ������� �� �� �ְ� �Ѵ�.
*  �Ϲ� ��ü���� ���α׷����� ������ ���� ������ ������ ����.
    *  ������ ���� �κ� : �������̽��� �߻� Ŭ����
    *  ������ ���� �κ� : Ŭ����
*  �ڹٽ�ũ��Ʈ�� �������� ���õ� ������ ������ ���������� �ʴ´�.
    *  �ٸ� ��ü���� ������ �޼��带 ȣ���ϴ� ����� �����Ѵ�.
    *  �ڹٽ�ũ��Ʈ�� type-safe �� �ƴϹǷ� ��� ������ ������ ����� �޼���� �Բ� ������ �� �ִ�.
```js
	var shape = function (){};
	shape.prototype.draw = function(){
		return "i am generic shape";
	}
    
	//circle
	var circle = function(){}
	circle.prototype = Object.create(shape.prototype);
	circle.prototype.draw= function(){
		return "i am a circle";
	}
    
	//triangle
	var triangle = function (){}
	triangle.prototype = Object.create(shape.prototype);
	triangle.prototype.draw= function(size){
		return "this is triangle";
	}
    
	//printing shapes
	var shapes = [new shape(), new circle(), new triangle(23)];
	shapes.forEach (function (shapeList){
		console.log(shapeList.draw());
	});
```
### Code Reuse
*  �ڹٽ�ũ��Ʈ���� �ڵ带 �����ϴ� ��� �� ���� �������� ����� ����̴�.
*  ��� �̿ܿ��� �޼��� ��������, �޼���� ��ü �����ϱ�, �Ӽ� ����, ���� ��ü�� �Ӽ� �ռ� ���� ����� �ִ�.  

**[? ����](#����)**

---

## Design Patterns
*  ������ �����̶� ���α׷� ���߿��� ���� ��Ÿ���� ������ �ذ��ϱ� ���� ����̴�.
*  ������ ����Ʈ���� ���� �������� �߰ߵ� ������ ���Ͽ츦 �����Ͽ� �̸��� �ٿ�, ���Ŀ� ���̿��ϱ� ���� ���·� Ư���� �Ծ��� ��� ������ ���̴�.
*  �˰���� ���� ���α׷� �ڵ�� �ٷ� ��ȯ�� �� �ִ� ���´� �ƴ�����, Ư���� ��Ȳ���� �������� ������ �ذ��ϴ� ����� ������ �ش�.

### Constructor pattern
*  ��ü ����
```js
var newObject = {};
// or
var newObject = Object.create(Object.prototype);
// or
var newObject = new Object();
```
*  ������ ����
```js
function person(firstName, lastName){  
  this.firstName = firstName;  
  this.lastName = lastName;  
  this.fullName = function(){
    return this.firstName + " " + this.lastName;
  }
}

var person1 = new person('Akash', 'Pal');
var person2 = new person('Black', 'Panther');
console.log(person1.fullName()); //"Akash Pal"
console.log(person2.fullName()); //"Black Panther"
console.log(person1); //{firstName: "Akash", lastName: "Pal", fullName: ?}
console.log(person2); //{firstName: "Black", lastName: "Panther", fullName: ?}
```
```js
function Car(model, year, miles) {
  this.model = model;
  this.year = year;
  this.miles = miles;
  
  this.toString = function() {
    return this.model + " has done " + this.miles + " miles";
  }
}

var civic = new Car("Honda Civic", 2009, 20000);
var mondeo = new Car("Ford Mondeo", 2010, 5000);

console.log(civic.toString());
console.log(mondeo.toString());
console.log(civic.toString === mondeo.toString); // false
```
*  �����ڿ� prototype ���
```js
function Car(model, year, miles) {
  this.model = model;
  this.year = year;
  this.miles = miles;
}

Car.prototype.toString = function() {
  return this.model + " has done " + this.miles + " miles";
}

var civic = new Car("Honda Civic", 2009, 20000);
var mondeo = new Car("Ford Mondeo", 2010, 5000);

console.log(civic.toString());
console.log(mondeo.toString());
console.log(civic.toString === mondeo.toString); // true
```

### Module pattern
```js
var personModule = (function(){
  var firstName;
  var lastName;
  
  return{
    setName(f,l){
      firstName = f;
      lastName = l;
    },
    getName(){
      return firstName + " " + lastName;
    }
  }
  
})();

personModule.setName('akash','pal')
personModule.getName() //"akash pal"
```
```js
var testModule = (function() {
  var counter = 0;
  
  return {
    incrementCounter: function() {
      return counter++;
    },
    resetCounter: function() {
      console.log("counter value prior to reset: " + counter);
      counter = 0;
    }
  };
})();

testModule.incrementCounter();
testModule.resetCounter();
```

### Revealing module pattern
```js
var personModule = (function(){
  var firstName;
  var lastName;
  
  function setName(f,l){
    firstName = f;
    lastName = l;
  }
  
  function getName(){
    return firstName + " " + lastName;
  }
  
  return {
    setName:setName,
    getName:getName
  };
})();

personModule.setName('akash','pal');
personModule.getName(); //"akash pal"
```

### Singleton pattern
```js
var singleton = (function() {
  var instance;
  
  function init(){    
    var name;

    this.setName = function(name) {
       this.name = name;
    }
    
    this.getName = function() {
      return this.name;
    }
    
    return {
      setName: setName,
      getName: getName
    }
  }
  
  function getInstance() {
    if(!instance) {
      instance = init();
    }
    return instance;
  }

  return {
    getInstance:getInstance
  }
})();

var one = singleton.getInstance();
var two = singleton.getInstance();

//the two instance are same
one == two //true

one.setName('Akash');
two.getName(); //"Akash"
```

### Observer pattern
*  ������ ������ �̺�Ʈ ó�� �� ���ӿ� ���ȴ�.
*  Subject�� Observer�� collection�� �����Ѵ�.
*  Subject�� �̺�Ʈ�� �߻��� ������ Observer���� �˸���.
*  ����
```js
function Subject() {
    this.observers = []; // Observers listening to the subject
    
    this.registerObserver = function(observer) {
        // Add an observer if it isn't already being tracked
        if (this.observers.indexOf(observer) === -1) {
            this.observers.push(observer);
        }
    };

    this.unregisterObserver = function(observer) {
        // Removes a previously registered observer
        var index = this.observers.indexOf(observer);
        if (index > -1) {
            this.observers.splice(index, 1);
        }
    };

    this.notifyObservers = function(message) {
        // Send a message to all observers
        this.observers.forEach(function(observer) {
            observer.notify(message);
        });
    };
}

function Observer() {
    this.notify = function(message) {
        // Every observer must implement this function
    };
}
```
*  ��뿹
```js
function Employee(name) {
    this.name = name;

    // Implement `notify` so the subject can pass us messages
    this.notify = function(meetingTime) {
        console.log(this.name + ': There is a meeting at ' + meetingTime);
    };
}

var bob = new Employee('Bob');
var jane = new Employee('Jane');
var meetingAlerts = new Subject();
meetingAlerts.registerObserver(bob);
meetingAlerts.registerObserver(jane);
meetingAlerts.notifyObservers('4pm');

// Output:
// Bob: There is a meeting at 4pm
// Jane: There is a meeting at 4pm
```
### Mediator pattern
*  ��ü ���� ���յ��� ���� ���� �������� ����� �ö󰣴�.
*  ������ ������ �̷� ������ ��ȭ�ϱ� ���� ������ �����̴�.
*  ������ ������ �Ϸ��� ��ü�� ��ȣ �ۿ��ϴ� ����� ĸ��ȭ �ϴ� ��ü �����̴�.
#### ����
![mediator_pattern_structure](./img/mediator_pattern_structure.PNG)
*  Mediator - �Ʒ� ���� �ڵ忡�� Chatroom
	*  Colleague ��ü�� ����ϱ� ���� �������̽��� ����
	*  Colleague ��ü�� ���� ������ ����
	*  ��� ���� �߾� ���� ����
*  Colleagues - �Ʒ� ���� �ڵ忡�� Participants
	*  Mediator�� �����ϴ� ��ü
	*  �� �ν��Ͻ��� Mediator�� ���� ������ ����
#### ���� �ڵ�
*  Chatroom�� ����Ͽ� ä�� ���ǿ� �����ϴ� �� ���� �����ڰ� �ִ�.
*  �� �����ڴ� Participant ��ü�� ǥ���ȴ�.
*  Participant�� ���ο��� �޽����� ������ Chatroom�� routing�� ó���Ѵ�.
*  �α� ����� ����� �����ϰ� ǥ���ϴ� helper�̴�.
```js
class Participant {
  constructor(name) {
    this.name = name;
    this.chatroom = null;
  }

  send(message, to) {
    this.chatroom.send(message, this, to);
  }

  receive(message, from) {
    log.add(from.name + " to " + this.name + ": " + message);
  }
}
 
let Chatroom = function() {
  let participants = {};

  return { 
    register: function(participant) {
      participants[participant.name] = participant;
      participant.chatroom = this;
    },
  
    send: function(message, from, to) {
      if (to) {                      // single message
        to.receive(message, from);    
      } else {                       // broadcast message
        for (let key in participants) {   
          if (participants[key] !== from) {
            participants[key].receive(message, from);
          }
        }
      }
    }
  };
};

// log helper
log = (function() {
    let log = '';

    return {
        add: msg => { log += msg + '\n'; },
        show: () => { alert(log); log = ''; }
    }
})();
 
function run() {
  let yoko = new Participant('Yoko'),
      john = new Participant('John'),
      paul = new Participant('Paul'),
      ringo = new Participant('Ringo'),
      chatroom = new Chatroom(),

  chatroom.register(yoko);
  chatroom.register(john);
  chatroom.register(paul);
  chatroom.register(ringo);

  yoko.send('All you need is love.');
  yoko.send('I love you John.');
  john.send('Hey, no need to broadcast', yoko);
  paul.send('Ha, I heard that!');
  ringo.send('Paul, what do you think?', paul);

  log.show();
}

run();
```
### Prototype pattern
*  ������Ÿ�� ������ ������Ÿ�� ����� ������� �Ѵ�.
*  ������Ÿ�� ��ü�� �����ڰ� �����ϴ� �� ��ü�� blueprint�� ���ȴ�.
*  ECMAScript5 ǥ�ؿ� ���ǵ� ���� ������Ÿ�� ��ӿ��� Object.create�� ����ؾ� �Ѵ�.
```js
function person(firstName,lastName){ 
  this.firstName = firstName;
  this.lastName = lastName;
}

person.prototype.fullName = function(){
  return this.firstName + " " + this.lastName;
}

var person1 = new person('Akash','Pal');
var person2 = new person('Black','Panther');

person1 //{firstName: "Akash", lastName: "Pal"}
person2 //{firstName: "Black", lastName: "Panther"}

person1.fullName() //"Akash Pal"
person2.fullName() //"Black Panther"
```
#### Object.create ���
```js
var myCar = {
  name: "Ford Escort",
  drive: function() {
    console.log("Weeee. I'm driving!");
  },
  panic: function() {
    console.log("Wait. How do you stop this thing?");
  }
};

var yourCar = Object.create(myCar);
console.log(yourCar.name);
```
### Commanmd pattern
*  ��� �����̶� ��û�� ��ü�� ���·� ĸ��ȭ�Ͽ� ����ڰ� ���� ��û�� ���߿� �̿��� �� �ֵ��� �޼��� �̸�, �Ű� ���� �� ��û�� �ʿ��� ������ ���� �Ǵ� �α�, ��� �� �� �ְ� �ϴ� �����̴�.
*  ���(command), ������(receiver), �ߵ���(invoker), Ŭ���̾�Ʈ(client)�� �� ���� �� �׻� ������.
*  ��û�� ������ �и����� ������ ������ �����Ѵ�.
*  �Ϸ��� �ൿ�� Ư�� Receiver�ϰ� ������ ���� ĸ��ȭ�ϰ� execute��� �޼ҵ� �ϳ��� �ܺο� �����Ѵ�.
*  ������ ��û �κа� ��û ���� �κ��� �и�, ���� ���, ����, �α� ������ �����ϴٴ� ���̴�.
```js
function add(x, y) { return x + y; }
function sub(x, y) { return x - y; }
function mul(x, y) { return x * y; }
function div(x, y) { return x / y; }
 
var Command = function (execute, undo, value) {
    this.execute = execute;
    this.undo = undo;
    this.value = value;
}
 
var AddCommand = function (value) {
    return new Command(add, sub, value);
};
 
var SubCommand = function (value) {
    return new Command(sub, add, value);
};
 
var MulCommand = function (value) {
    return new Command(mul, div, value);
};
 
var DivCommand = function (value) {
    return new Command(div, mul, value);
};
 
var Calculator = function () {
    var current = 0;
    var commands = [];
 
    function action(command) {
        var name = command.execute.toString().substr(9, 3);
        return name.charAt(0).toUpperCase() + name.slice(1);
    }
 
    return {
        execute: function (command) {
            current = command.execute(current, command.value);
            commands.push(command);
            log.add(action(command) + ": " + command.value);
        },
 
        undo: function () {
            var command = commands.pop();
            current = command.undo(current, command.value);
            log.add("Undo " + action(command) + ": " + command.value);
        },
 
        getCurrentValue: function () {
            return current;
        }
    }
}
 
// log helper
 
var log = (function () {
    var log = "";
 
    return {
        add: function (msg) { log += msg + "\n"; },
        show: function () { alert(log); log = ""; }
    }
})();
 
function run() {
    var calculator = new Calculator();
 
    // issue commands
 
    calculator.execute(new AddCommand(100));
    calculator.execute(new SubCommand(24));
    calculator.execute(new MulCommand(6));
    calculator.execute(new DivCommand(2));
 
    // reverse last two commands
 
    calculator.undo();
    calculator.undo();
 
    log.add("\nValue: " + calculator.getCurrentValue());
    log.show();
}
```
### Facade pattern
*  �ۻ�� ������ �ϳ� �̻��� ���� �ý��ۿ��� ������ ������κ��� Ŭ���̾�Ʈ�� ��ȣ�ϴ� �������̽��� �����Ѵ�.
*  �ۻ�� ������ ������ Ŭ���̾�Ʈ�� ���� �ý��� �Ǵ� ��Ŷ�� ���� ����� �� �ְ� �ϴ� ��� �������̽�(�Ӽ�, �޼���)�� �����ϴ� ���̴�.
```js
var Mortgage = function(name) {
    this.name = name;
}
 
Mortgage.prototype = {
 
    applyFor: function(amount) {
        // access multiple subsystems...
        var result = "approved";
        if (!new Bank().verify(this.name, amount)) {
            result = "denied";
        } else if (!new Credit().get(this.name)) {
            result = "denied";
        } else if (!new Background().check(this.name)) {
            result = "denied";
        }
        return this.name + " has been " + result +
               " for a " + amount + " mortgage";
    }
}
 
var Bank = function() {
    this.verify = function(name, amount) {
        // complex logic ...
        return true;
    }
}
 
var Credit = function() {
    this.get = function(name) {
        // complex logic ...
        return true;
    }
}
 
var Background = function() {
    this.check = function(name) {
        // complex logic ...
        return true;
    }
}
 
function run() {
    var mortgage = new Mortgage("Joan Templeton");
    var result = mortgage.applyFor("$100,000");
 
    alert(result);
}
```
### Factory pattern
*  ���丮 ������ ������ ����� ��ü�� �ݺ� �����ϴ� ���̴�.
*  ����ڰ� ��ü���� Ÿ���� ���� ��ü�� ������ �� �ְ� ���ش�.
```js
function Factory() {
    this.createEmployee = function (type) {
        var employee;
 
        if (type === "fulltime") {
            employee = new FullTime();
        } else if (type === "parttime") {
            employee = new PartTime();
        } else if (type === "temporary") {
            employee = new Temporary();
        } else if (type === "contractor") {
            employee = new Contractor();
        }
 
        employee.type = type;
 
        employee.say = function () {
            log.add(this.type + ": rate " + this.hourly + "/hour");
        }
 
        return employee;
    }
}
 
var FullTime = function () {
    this.hourly = "$12";
};
 
var PartTime = function () {
    this.hourly = "$11";
};
 
var Temporary = function () {
    this.hourly = "$10";
};
 
var Contractor = function () {
    this.hourly = "$15";
};
 
// log helper
var log = (function () {
    var log = "";
 
    return {
        add: function (msg) { log += msg + "\n"; },
        show: function () { alert(log); log = ""; }
    }
})();
 
function run() {
    var employees = [];
    var factory = new Factory();
 
    employees.push(factory.createEmployee("fulltime"));
    employees.push(factory.createEmployee("parttime"));
    employees.push(factory.createEmployee("temporary"));
    employees.push(factory.createEmployee("contractor"));
    
    for (var i = 0, len = employees.length; i < len; i++) {
        employees[i].say();
    }
 
    log.show();
}
```
**[? ����](#����)**

---

## Partial Applications, Currying, Compose and Pipe
### Partial Applications
*  ���� ���� ���ڸ� �޴� �Լ��� �Ϻ� ���ڸ� ������ �Լ��� ����� ����̴�.
*  �ߺ��� �ڵ带 ���̰� ������ �Լ����� ���� �������� ���� �� �ִ�.
*  �Լ��� ������ ������ ���ڰ� �־��� ������ �ڷ� �̷� �� �ִ�.
```js
var plus = function(a, b, c) {
  return a + b + c;
};

var plusa = plus.bind(null, 1);
plusa(2, 3); // 6
var plusb = plusa.bind(null, 2);
plusb(4); // 7
var plusab = plus.bind(null, 1, 3);
plusab(5); // 9
```
```
function ajax(endPoint = '', search = {}) {
  // ...
  return Promise.resolve(res);
}

const getUser = ajax.bind(null, '/user');
getUser({ id: 'A1' }).then((res) => {
    // ...
  })

const getAdminUser = ajax.bind(null, 'user', { authority: 'admin' });
getAdminUser().then((res) => {
    // ...
  })
```
### Currying
*  ���� ���� ���ڸ� �޴� �Լ��� ���� �ϳ��� �޴� �Լ� ���� ���� ���������� ó���ϴ� ����̴�.
*  ��) `doSomething(1, "Hello", true)` ��� `doSomething(1)("Hello")(true)`�� ���� ȣ���Ѵ�.
*  �ߺ��� �ڵ带 ���̰� ������ �Լ����� ���� �������� ���� �� �ִ�.
*  �Լ��� ������ ������ ���ڰ� �־��� ������ �ڷ� �̷� �� �ִ�.

```js
// Arrow function
const add = x => y => x + y;
// Normal function
function add(x) {
  return function(y) {
    return x + y;
  }
}

const addFive = add(5);
addFive(7); // 12
```
*  �������� ����
```js
var server = function(address) {
  return function(loginInfo) {
    // ���� ���� ������
    var loginToken = //
    return function(request) {
      // loginToken�� ����ؼ� ������ Ư�� request��û�ϴ� �ڵ�
    };
  };
};

var connection = server("http://address");
var request = connection({"username": "kevin", "password": "1111"});
var request2 = connection({"username": "tom", "password": "1234"});
```
### Compose, Pipe
*  �Լ��� ���α׷����� �⺻ ���̵��� �Լ����� ���� ���̴�.
*  �� ���� ����� �����ϴ� ���� �Լ����� �����Ͽ� ������ ����� �����Ѵ�.
*  �̰��� �ٷ� �Լ��� �ռ�(function composition)�̴�.
*  �̰��� �� �Լ��� ����� �ٸ� �Լ��� �Է����� ���������ν� �޼��ȴ�.
#### �Լ��� �ռ�
```js
const addTwo = x => x + 2;
const multiplyByFour = x => 4 * x;
const devideByTwo = x => x / 2;

const composed = X => deviceByTwo(addTwo(multiplyByFour(X)));
```
���� ���� �Լ��� �ռ��ϴ� ���� �б� ��Ʊ� ������ �������� �ʴ�.
#### compose()
*  compose()�� �Լ����� ���ڷ� �޴´�.
*  data flow�� �����ʿ��� �����̴�.
*  ������ �Ʒ��� ����.
```js
const compose = (...fns) => {
  return x => {
    return fns.reduceRight((y, f) => f(y), x)
  }
}
```
*  ������ �Ʒ��� ����.
```js
const addTwo = x => x + 2;
const multiplyByFour = x => 4 * x;
const devideByTwo = x => x / 2;

const composeFunc = compose(devideByTwo, multiplyByFour, addTwo)
const result = composeFunc(3)
// 10 <-- devideByTwo(20) <-- 20 <-- multiplyByFour(5) <-- 5 <-- addTwo(3) <-- 3
```
#### pipe()
*  pipe()�� compose()��  data flow�� ���ʿ��� �������̶�� �� �ܿ� �����ϴ�.
*  ������ �Ʒ��� ����.
```js
const pipe = (...fns) => {
  return x => {
    return fns.reduce((y, f) => f(y), x)
  }
}
```
*  ������ �Ʒ��� ����.
```js
const addTwo = x => x + 2;
const multiplyByFour = x => 4 * x;
const devideByTwo = x => x / 2;

const pipeFunc = pipe(addTwo, multiplyByFour, devideByTwo)
const result = pipeFunc(3)
```
**[? ����](#����)**

---

## Clean Code
https://github.com/qkraudghgh/clean-code-javascript-ko  

**[? ����](#����)**

---