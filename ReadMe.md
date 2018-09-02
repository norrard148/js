
# promise 사용

<pre><code>
function start1 () {
        return new Promise(function(resolve, reject) {
            console.log("start1")
        });
}

function start2 () {
        return new Promise(function(resolve, reject) {
            console.log("start2")
        });
}
            
start1().then(start2())
</code></pre>

#  const / let

ES5까지 쓰이고 있던 변수 선언 방식인 var이 비효율적이거나 구체적이지 못한 한계가 있어 ES6부터 바뀌게 된다. const는 쉽게 말해서 상수이고, let은 단순 변수를 말한다. const는 한번 선언하면 값을 바꿀 수없다는 말이다. 다만, array나 hash 형태의 자료형은 그 안의 내용물은 바꿀 수 있다. let은 한번 선언했다가 여러번 다시 값을 바꿔줄 수 있다.

<pre><code>
    var a;

    const b;

    let c;
</code></pre>

# Arrow function

Es6에 들어오면서 함수 선언 방식이 하나 추가되었다. 보통은,

<pre><code>
    var functionName = function () {

    }
</code></pre>

이지만, 이제 

<pre><code>
    var functionName () => {

    }
</code></pre>

가 가능하다.

# Spread Operators

<pre><code>
    ...
</code></pre>

가 Spread Operator이다. 별거 없고, 그냥 ...something 식으로 작성하면 something을 유효하게 나열해주는 것이다.

<pre><code>
    const a =  ['call, 'your']
    const b = ['nono', ...a]
</code></pre>

# Array Method

mdn 참고

.map()

.map() 메소드는 배열 내의 모든 요소 각각에 대하여 제공된 함수(callback)를 호출하고, 그 결과를 모아서 새로운 배열을 반환합니다.

<pre><code>
var array1 = [1, 4, 9, 16];

// pass a function to map
const map1 = array1.map(x => x * 2);

console.log(map1);
// expected output: Array [2, 8, 18, 32]
</code></pre>

.slice()

.slice()는 특정 요소의 일정 부분을 삭둑 잘라내는 역할을 한다.

<pre><code>
var uint8 = new Uint8Array([1,2,3]);
uint8.slice(1);   // Uint8Array [ 2, 3 ]
uint8.slice(2);   // Uint8Array [ 3 ]
uint8.slice(-2);  // Uint8Array [ 2, 3 ]
uint8.slice(0,1); // Uint8Array [ 1 ]
</code></pre>

.splice()

splice() 는 어떤 문자열을 어떠 특정 문자열이 등장할때마다 쪼갠 뒤, 그 쪼갠 조각들을 각각 배열의 요소로 만들어 배열로 만들어주는 것이다.
<pre><code>
const a = "go/mo/do"
const b = a.splice("/")
</code></pre>

.filter()

filter() 메소드는 제공된 함수로 구현된 테스트를 통과하는 모든 요소가 있는 새로운 배열을 만듭니다.

<pre><code>
var words = ['spray', 'limit', 'elite', 'exuberant', 'destruction', 'present'];

const result = words.filter(word => word.length > 6);

console.log(result);
// expected output: Array ["exuberant", "destruction", "present"]
</code></pre>

.reduce()

reduce()메서드는 누산기(accumulator)와 배열의 각 요소(왼쪽에서 오른쪽으로)에 대해 하나의 단일 값(single value)으로 줄이는 함수를 적용합니다.


<pre><code>
const array1 = [1, 2, 3, 4];
const reducer = (accumulator, currentValue) => accumulator + currentValue;

// 1 + 2 + 3 + 4
console.log(array1.reduce(reducer));
// expected output: 10

// 5 + 1 + 2 + 3 + 4
console.log(array1.reduce(reducer, 5));
// expected output: 15

//정확한 .reduce() 작동방식은 이것이다.
[0, 1, 2, 3, 4].reduce(function(accumulator, currentValue, currentIndex, array) {
  return accumulator + currentValue;
});
</code></pre>

# export / import

class, module을 다른 파일에 수출 수입할 때 쓴다. 말 그대로, 한 js 파일 내에서 다른 js 파일에서 사용할 수 있도록 허용할 수 있게 만들 때 사용한다. 오직, export된 놈만 import할 수 있다.


main.js 파일

<pre><code>
 const a = 11;

 export defualt a;
</code></pre>

introduction.js 파일

<pre><code>
import a from '/main.js';

console.log(a);
</code></pre>