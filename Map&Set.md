# Set

The Set object lets you store unique values of any type, whether primitive values or object references.

## size
size
The size accessor property returns the number of (unique) elements in a Set object.

~~~

const set1 = new Set();
const object1 = {};

set1.add(42);
set1.add('forty two');
set1.add('forty two');
set1.add(object1);

console.log(set1.size);
// Expected output: 3

~~~
## add()
Inserts a new element with a specified value in to a Set object, if there isn't an element with the same value already in the Set.

~~~

const set1 = new Set();

set1.add(42);
set1.add(42);
set1.add(13);

for (const item of set1) {
  console.log(item);
  // Expected output: 42
  // Expected output: 13
}

~~~
## clear()
Removes all elements from the Set object.

~~~
const set1 = new Set();
set1.add(1);
set1.add('foo');

console.log(set1.size);
// Expected output: 2

set1.clear();

console.log(set1.size);
// Expected output: 0

~~~
## delete()
Removes the element associated to the value and returns a boolean asserting whether an element was successfully removed or not. Set.prototype.has(value) will return false afterwards.

~~~

const set1 = new Set();
set1.add({ x: 10, y: 20 }).add({ x: 20, y: 30 });

// Delete any point with `x > 10`.
set1.forEach((point) => {
  if (point.x > 10) {
    set1.delete(point);
  }
});

console.log(set1.size);
// Expected output: 1

~~~
## has()
Returns a boolean asserting whether an element is present with the given value in the Set object or not.

~~~
const set1 = new Set([1, 2, 3, 4, 5]);

console.log(set1.has(1));
// Expected output: true

console.log(set1.has(5));
// Expected output: true

console.log(set1.has(6));
// Expected output: false

~~~