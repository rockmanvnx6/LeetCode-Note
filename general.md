# General Notes

<Note>

This contains my personal general note I learned from my mistakes. Some of them are just for **Javascript**

</Note>

#### 1. When comes to solving a LinkedList, **avoid comparing** `next` **node**

For example, don't compare `a.next` with `b.next`. Just compare `a` with `b`, and use

```js
a = a.next;
b = b.next;
```
---

#### 2. When comes to solving a Tree, **avoid comparing children node**

Similar to the above rule, if in the situation when you need to compare `node.left` and `node.right`, create another function to do it:

```js
function compare(node,min,max) {
    // compare a node with min and max
}
```
---

#### 3. Use direct reference when dealing with Object instead of assigning a variable for it

<Note type="warning"> This might be just for **javascript**</Note>

When dealing with object, for example

```js {highlight: [6,8]}
function example(nums) {
    let memo = {};
    for(let i = 0; i < nums.length; i++) {
        let value = memo[nums[i]];
        if(value) {
            value += 1;
        } else {
            value = 1;
        }
    }
}
```

The highlighted variable are *copies of memo*. Therefore, it wouldn't work. Instead, we have to explicitly call `memo[nums[i]]`

```js {highlight: [6,8]}
function example(nums) {
    let memo = {};
    for(let i = 0; i < nums.length; i++) {
        let value = memo[nums[i]];
        if(value) {
            memo[nums[i]] += 1;
        } else {
            memo[nums[i]] = 1;
        }
    }
}
```
---

#### 4. When use mod in Javascript, **write your own mod function**
<Note type="warning"> This might be just for **javascript**</Note>

```js
function mod(n,m) {
    return ((n%m)+m)%m
}
// or
function mod(n,m) {
    return n - (m * Math.floor(n/m))
}
```

---

#### 5. Always use `MAX_SAFE_INTEGER` and `MIN_SAFE_INTEGER` for max min constant

<Note type="warning"> This might be just for **javascript**</Note>

Usage:

```js
Number.MAX_SAFE_INTEGER;
Number.MIN_SAFE_INTEGER;
```

---

#### 6. Avoid using `while(a || b)`

This can lead to clumsy code, for example, you might face:

```js
if(!a) { return b }
if(!b) { return a }
while(a || b) {
    if (!a) {...}
    else if (!b) {...}
}
```

Just instead use

```js
while(a && b) {
    ...
}
    
return a || b;
```

---

#### 7. Splice

Syntax: `arr.splice(start,remove_count_from_start,replace)` this is start, end **exclusive**. And will be modified directly to the array itself.

It will return the deleted value.

```js
arr = [1,2,3,4,5,6,7]
arr.splice(2,4, 'apple')
// [1,2,'apple',7]
```

---

#### 8. Sorting ascending, descending

**a. To sort ascending**

```js
arr.sort((a,b) => a-b);
// 1, 2, 3, 4, 5, 6
```

**b. To sort descending**

```js
arr.sort((a,b) => b-a);
// 6, 5, 4, 3, 2, 1
```

---

#### 9. Object-key sorting

```js
let map = {};
...
let sortedKeys = Object.keys(map).sort((a,b) => a-b);
```

---

#### 10. String array sorting

```js
arr = [ 'zscc', 'apple', 'caca', 'bbb' ];
```

**a. To sort ascending**

```js
arr.sort((a,b) => a > b ? 1 : -1);
```

**b. To sort descending**

```js
arr.sort((a,b) => b > a ? 1: -1);
```

---

#### 11. Object check key is inside.

```js
let map = {};
...
if(map.hasProperty(name)) {
    ...
}
```

---

#### 12. Array unshift(), shift(), push(), pop()

**a. Removing**

-   shift(): remove from **front**. Return the **item** that you are removing

    ```js
    arr = [9,1,2,3,4,5]
    let remove = arr.shift(); // 9
    console.log(arr) // [1,2,3,4,5]
    ```

-   pop(): remove from **back**. Return the **item** that you are removing

    ```js
    arr = [9,1,2,3,4,5]
    let remove = arr.pop(); // 5
    console.log(arr) // [9,1,2,3,4]
    ```

**b. Adding**

-   unshift(): add from **front**. Return the **length** of the array after added

    ```js
    arr = [9,1,2,3,4,5]
    let length = arr.unshift(0); // 7
    console.log(arr) // [0,9,1,2,3,4,5]
    ```

-   push(): add from **back**. Return the **length** of the array after added

    ```js
    arr = [9,1,2,3,4,5]
    let length = arr.push(0); // 7
    console.log(arr) // [9,1,2,3,4,5,0]
    ```

    