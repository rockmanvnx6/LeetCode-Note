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




