# Day3 使用 Javascript 更新 CSS 變數

## 一些用到的東西
- forEach: 不會回傳新陣列的 map() 
```
const arr = [1, 2, 3]
arr.forEach(addWord) 
// forEach 需要一個操作陣列的 callback function
// callback function 可使用資料本身（arr）、索引（index）與資料的各項目（item）

function addWord(item, index) {
    arr[index] = item + '個'
}

console.log(arr) // ['1個', '2個', '3個']

```

- css filter: 濾鏡效果，包含模糊（blur）、對比(contrast)、色階轉換（hue-rotate）、輪廓陰影（drop-shadow），族繁不及備載直接查比較快。部分效果可以混用
- data-*: 直接將資料/值綁定元素，可用 `dataset` 與 `getAttribute` 取得該屬性的資料
- style.setProperty(): 直接設定樣式的 property ，參數有屬性與值，還可以調整優先層級
```
style.setProperty(propertyName, value, priority)
ex. 
element.style.setProperty('border', '1px solid red')
等於 element.style.border = '1px solid red'
```
- setProperty 也可以修改 CSS 變數： [來源](https://css-tricks.com/updating-a-css-variable-with-javascript/)
```
let root = document.documentElement;

root.addEventListener("mousemove", e => {
  root.style.setProperty('--mouse-x', e.clientX + "px");
  root.style.setProperty('--mouse-y', e.clientY + "px");
});
```
- Document.documentElement 會回傳目前文件的根元素
- mousemove: The pointer is moved over an element 