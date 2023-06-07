# 筆記

解法前半段和影片差不多，都是使用事件監聽器觸發事件處理函數播放音效、讓網頁對應按鍵的方塊增加預先寫在 CSS 檔案內的效果。

## 解題步驟

我的想法：
按下按鍵 > 觸發事件處理函數 > 事件函數處理：(1)播放音樂、(2)增加畫面對應按鍵區域的效果 > 移除對應按鍵區域的效果

- 安裝事件監聽器： `window.addEventLister('event', function);`
- 綁定箭頭函數執行對應的工作（事件處理函數）
- 透過事件找出按下按鍵的資料並儲存在變數內
  ＊這次的需求比較簡單，所以可以宣告函數把取得的按鍵資料裝在變數內，但如果功能變的更複雜，直接使用 e.keyCode 可以避免變數作用域被污染的問題，也可以減少記憶體的儲存空間
- 抓取 audio 元素中 data-key 和按鍵資料相符的音效：`const audioNode = document.querySelector(`audio[data-key = "${keyCode}"]`);`
    ＊ querySelector 是 HTML DOM API ，如果要讓 js 的資料可以送入該 API 中，可以使用模板語法 `HTML 的元素要使用的： ${jsVariable}` 
- 抓取對應的 div 元素
- 增加 class 屬性： `node.classList.add();` 
- 處理播放音效的事情：
    1. 操作 dom node 媒體播放： `node.play();`
    2. 處理連續播放音效問題
        使用 `HTMLMediaElement.currentTime` ：該屬性以秒為單位回傳該媒體元素的播放時


以下和影片的解法有差異

keydown ：播放音效、對應的區塊增加 CSS 效果
連續 keydown ：連續播放音效、 CSS 效果持續（沒有任何移除 CSS 效果的指令）
=> 移除 CSS 效果 = 沒有播放音效時 = keyup 的時候

- 使用 `node.classList.remove()` 移除 CSS

## 補充

鍵盤事件：

- keydown ：按下鍵盤的瞬間可以取得該對應鍵盤的資料（keyCode）。可用 console.log(e) 去找
- keypress ：只對取得有值的按鍵有效
- keyup ：放開鍵盤的瞬間

[KeyboardEvent: key property](https://developer.mozilla.org/en-US/docs/Web/API/KeyboardEvent/key)



  window.addEventListener('keydown', (e) => {
      // 儲存按下按鍵的資訊
      const keyCode = e.keyCode;

      // 透過 querySelector 抓取 data-key 屬性與 keyCode 值相同的 audio 元素
      const audioNode = document.querySelector(`audio[data-key = "${keyCode}"]`);
      // 透過 querySelector 抓取 data-key 屬性與 keyCode 對應的 div 位置
      const keyDiv = document.querySelector(`.key[data-key = "${keyCode}"]`);

      // 選到該 div 時 className 會增加 playing 顯示黃色框框
      keyDiv.classList.add('playing');

      // 處理連續按相同按鈕只會出現一次音效的問題 
      // 使用 HTMLMediaElement.currentTime ：該屬性以秒為單位回傳該媒體元素的播放時間
      // 對應到 react ref 存放聲音的 id ，但
      audioNode.currentTime = 0;
      audioNode.play();

      // 聲音播放結束後移除 className 
      // keyDiv.classList.remove('playing');
      window.addEventListener('keyup', (e) => {
        keyDiv.classList.remove("playing");
      })
  })