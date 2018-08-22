# Simple emoji manager panel

> 😄 Pure javascript class with jRun library

This project is developed for fanavard contest 


- draggable floating menu
- rtl-ltr support
- styling support
- instancable selectors
- emoji can modified in a json file :
```json
/**
 * List of emoji icons in json
 * @type {*[]}
 */
var jsonOfEmojies = [
    {
        "keywords": "score - perfect - numbers - century - exam - quiz - test - pass - hundred ",
        "faKeywords": "نمره - کامل - اعداد - قرن - امتحان - مسابقه - آزمون - عبور - صد - 100 ",
        "name": "100 ",
        "content": "💯"
    }, {
        "keywords": "numbers - blue-square ",
        "faKeywords": "اعداد - مربع آبی - 1234 ",
        "name": "1234 ",
        "content": "🔢"
    },
     ...
];
```
- floating panel feature 
- configable `EmojiManager` class

```javascript
var defaultOptions = {
    selector: '.searchEmoji',
    draggable: true,
    title: 'انتخاب شکلک',
    background: '#F00000',
    textColor: '#fff',
    kindOfSearch: 'all',   // first , end
    afterMenuShow: function () {},
    afterChoose: function () {},
    afterClose: function () {},
    rtl: true,
    position: 'absolute',    // absolute , fixed-top-left , fixed-top-right , fixed-bottom-left , fixed-bottom-right
    debug: false
};
```

We use jRun to handle files lazyLoad so we have :
```javascript
jRun.init([
    {url: "emoji/emoji.min.css"},
    {url: "emoji_json", kind: "Fanavard"},
    {url: "linerIcons.css", kind: "Icons"},
    {url: "emoji", kind: "Fanavard"}
], function () {

    // On input
    new EmojiManager({
        selector: '#inputEmojiManager',
        background: '#6E8FFF',
        draggable: true,
        rtl: true,
        title: 'انتخاب شکلک'
    });


    // On textarea
    new EmojiManager({
        selector: '#textAreaEmojiManager',
        background: '#5de83d',
        draggable: true,
        rtl: true,
        title: 'Emojiyi seç'
    });

    // On textarea
    new EmojiManager({
        selector: '#textAreaEmojiManagerRTL',
        background: '#2b6c1c',
        draggable: true,
        rtl: true,
        title: 'شکلک انتخاب المغی'
    });


    // On contentEditable
    new EmojiManager({
        selector: '#divEmojiManager',
        draggable: true,
        background: '#F00000',
        afterChoose: function (emojiName) {
            log("emoji : " + emojiName);
        },
        position: 'fixed-bottom-left'
    });
	

	document.getElementById("choosePositionEmojiManger").addEventListener("change" ,  function(e){
		SelectPosition.settings.position = this.value;
	});

});
```
- custom good events :
```javascript
    afterMenuShow: function () {},
    afterChoose: function () {},
    afterClose: function () {},
```

### Run locally

just open `index.html` file

**improve this class ?**

Go to `public/Javascript` enjoy working with my codes :)


### TODO 

- [ ] Use `webpack` and add class to `npm`
- [ ] Fix floating bug with `ltr` and `rtl` complex text
- [ ] Add little documentation here  
