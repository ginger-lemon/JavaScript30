# Day 5: flex 燈箱

- flex: flex-grow | flex-shrink | flex-basis
- flex-basis: 定義 X 軸（寬度）尺寸
- flex-shrink: 元素縮小，只在全部元素的預設寬度大於上層容器時才會根據設定的尺寸縮小
- flex-grow: 元素放大（ flex 尺寸是扣掉其他設定後瀏覽器自動根據比例分配的）
- transitionend 事件：完成 CSS 的 transition
- e.target: 最初觸發的 DOM 物件
- e.timeStamp: 事件物件建立的時間
- e.type: 事件類型
- element.classList.toggle: toggle 檢查該 class 是否存在；有會移除、沒有會加入，就不用手動設定
- e.propertyName: transition 事件中的處理過渡效果的屬性