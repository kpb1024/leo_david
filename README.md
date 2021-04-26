# leo_david

```
{
  "manifest_version": 2,

  "name": "DanMu Filter",
  "description": "This extension filters bad Danmu.",
  "version": "1.0",

  "permissions": [
    "*://*.egame.qq.com/*",
    "webRequestBlocking",
    "webRequest",
    "storage", "activeTab"
  ],
  "background": {
    "service_worker": "background.js"
  },
  "browser_action": {
    "default_icon": "pics/xiaoxiao.png"
  }
}
```

```
let color = '#3aa757';

chrome.runtime.onInstalled.addListener(() => {
    chrome.storage.sync.set({ color });
    console.log('Default background color set to %cgreen', `color: ${color}`);
});


function nodeInsertedCallback(event) {
    let t = event.target;
    let spans = t.getElementsByTagName("span");
    let localName = ""
    let localContent = ""
    for (const spanObj in spans) {
        switch (spanObj.className) {
            case "name":
                localName = spanObj.innerText;
            case "content":
                localContent = spanObj.innerText;

        }
    }
    console.log(localName+""+localContent)
}


function test(event) {
    if (cnt-- > 0) {
        c = event.target
    }
}

const chat_list = document.getElementsByClassName("chat-content-ul").item(0);

chat_list.addEventListener('DOMNodeInserted', nodeInsertedCallback);

for (let i = 0; i < spans.length; i++) {
    console.log(spans[i].innerText)
}
```
