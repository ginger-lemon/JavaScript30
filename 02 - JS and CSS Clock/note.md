# D2 筆記

- transform ：預設是以元素中心點作為基準點
- transform-origin ：改變元素預設的基準點，需搭配 transform 使用
- transitiion-timing-function ：調整動畫時間效果
- element.style.... ：設定該元素樣式

## 指針動畫問題

- 指針會因為秒數、分數使得角度歸零，造成角度上的落差（354 -> 0），因此會有往回跑一圈的動畫效果，需於
- 直接針對不同元素的動態新增樣式調整對應的動畫效果，避免影響到共同樣式

