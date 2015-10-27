# Rx**Fx**
---
# **Flux** with **RxJS**
---
# But **first!**
---
# Array **Iteration** Methods
---
# Yay 4 **Immutability**
---
```javascript
arr.map()
arr.filter()
arr.flatMap()
arr.reduce()
arr.zip()
```
---
# `.map()`

**Creates a new array** with the results of calling a provided function on every element in this array.
---
```javascript
const arr = [34, 3, 6];
const newArr = arr.map((item) => item * 2);
// → [68, 6, 12]
```
---
# `.filter()`

Creates a new array with all of the elements of this array **for which the provided filtering function returns true**.
---
```javascript
const arr = [34, 3, 6];
const newArr = arr.map((item) => item > 3);
// → [34, 6]
```
---
# [`.flatMap()`](http://jsbin.com/sanuza/3/edit?html,js,console)

Creates a new **flattened array** with the results of calling a provided function **which returns an array on every element in this array**.
---

```javascript
Array.prototype.concatAll = () => {
	const results = [];

	this.forEach((subArray) => {
		results.push.apply(results, subArray);
	});

	return results;
};
```

```javascript
Array.prototype.flatMap = (projectionFunctionThatReturnsArray) => {
	return this.map((item) => {
			return projectionFunctionThatReturnsArray(item);
		})
		// apply the concatAll function to flatten the two-dimensional array
		.concatAll();
};
```
---
```javascript
const movieLists = [{
	name: "New Releases",
	videos: [{ "id": 70111470, /* ... */ }, { "id": 654356453, /* ... */ }]
},
{
	name: "Dramas",
	videos: [{ "id": 65432445, /* ... */ }, { "id": 675465, /* ... */ }]
}];

const newArr = movieLists.flatMap((movieList) => {
	return movieList.videos.map((video) => video.id);
});
// → [70111470, 654356453, 65432445, 675465]
```
---
# `.reduce()`

Apply a function against an accumulator and each value of the array (from left-to-right) **as to reduce it to a single value**.
---
```javascript
const boxarts = [
	{ width: 200, height:200, url:"http://cdn-0.nflximg.com/images/2891/Fracture200.jpg" },
	{ width: 150, height:200, url:"http://cdn-0.nflximg.com/images/2891/Fracture150.jpg" },
	{ width: 425, height:150, url:"http://cdn-0.nflximg.com/images/2891/Fracture425.jpg" }
];

const boxartsUrls = boxarts.reduce((acc, curr) => {
    if (acc.width * acc.height > curr.width * curr.height) {
      return acc;
    } else {
      return curr;
    }
  })
  .map((boxart) => {
    return boxart.url;
  });

console.log(boxartsUrls);
// → ["http://cdn-0.nflximg.com/images/2891/Fracture425.jpg"]
```
---
# `.zip()`

Combine multiple Arrays together via a specified function and return **a new array with the combined values**.
---
```javascript
Array.zip = (left, right, combinerFunction) => {
	let counter;
	const results = [];

	for(counter = 0; counter < Math.min(left.length, right.length); counter++) {
		results.push(combinerFunction(left[counter],right[counter]));
	}

	return results;
};
```
---
# [Zip Example](http://jsbin.com/vucamu/19/edit?js,console)
---
# Observables
---
# Events are collections **over time**
---
# Observables can also be called **streams**
---
```javascript
[{ x: 12, y: 32}, { x: 45, y: 62}, { x: 22, y: 33}]

{ x: 12, y: 32}...{ x: 45, y: 62}...{ x: 22, y: 33}
```
---
# [Example](http://jsbin.com/vogahe/8/edit?js,console,output)
---
# Streams are ubiquitous **anything can be a stream**
---
# You can use **array functions** on streams
---
# **Doubleclick** Example
---
# [![](/doubleclick.png)](http://jsbin.com/sitovu/11/edit?js,console,output)
---
# [Drag & Drop Example](http://jsbin.com/tihovi/9/edit?js,console,output)
---
# [RxJS Subject](http://jsbin.com/xeditu/6/edit?js,console)
---
# **RxFx**
---
![](/flux-diagram.png)
---
# Dive into **teh codez**
