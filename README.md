# Audio player

Du ska göra en egen musikspelare som spelar julmusik med hjälp av [audio-taggen](https://www.w3schools.com/tags/ref_av_dom.asp) med **custom controls** och **styling**.
Du kommer att hämta musik ifrån Spotify:s API.

Du ska använda dig av Redux för att göra API-anrop och spara i din store.

## Instruktioner

Starta med att köra `npx create-react-app {namn på din app}`

Kör sedan `npm install redux react-redux redux-thunk --save`


## Spotify API

Innan du kommer kunna göra ett anrop till Spotify:s API behöver du hämta en token
från detta API: https://blooming-reef-63913.herokuapp.com/api/token.

Exempel request:
```
  const response = await fetch('https://blooming-reef-63913.herokuapp.com/api/token');
  const data = await response.json();
```

Exempel response:
```
{"token":"BQDurLRk0q-B_bN_xrL0rPFQzKPICZ9Dd54bSRXTF4XNisynDWnIxY3hzMMheWFk_O9cr380o61UMJudbEM"}
```

Du ska använda dig av denna endpoint ```https://api.spotify.com/v1/search```

API-konsol: https://developer.spotify.com/console/get-search-item/

API-dokumentation: https://developer.spotify.com/documentation/web-api/reference/search/search/

Exempel request:
```
  const response = await fetch("https://api.spotify.com/v1/search?q=spirit%20of%20the%20season&type=track", {
  "headers": {
    "authorization": "Bearer BQDurLRk0q-B_bN_xrL0rPFQzKPICZ9Dd54bSRXTF4XNisynDWnIxY3hzMMheWFk_O9cr380o61UMJudbEM"
  }
});;
  const data = await response.json();
```


## Audio-taggen

```html
<audio id="player">
    <source src="https://p.scdn.co/mp3-preview/ad04264bcbf286030f90895dacdc2af00e586c99?cid=774b29d4f13844c495f206cafdad9c86" />
</audio>
```

## Funktionalitet

* **play** ska starta ljudfilen, den ska även bytas ut mot *pause* symbolen vid spelning
* **pause** ska pausa ljudfilen, den ska även bytas ut mot *play* symbolen vid pausning


### Level up
* **backward** ska hoppa tillbaka 10 sekunder i ljudfilen
* **forward** ska hoppa framåt 10 sekunder i ljudfilen
* **progressbar** ska visa ljudfilens framsteg

## Användbara egenskaper på audio-objektet

|prop|desc|
|---|---|
|currentTime|visar / anger aktuell tid i sek. |
|volume|visar / anger ljudstyrka mellan 0 - 1. |
|duration|visar ljudfilens längd i sek. | 

```js
let el = document.querySelector('audio');

el.currentTime  // returnerar 12.345
el.duration     // returnerar 182.11
el.volume       // returnerar 0.63
```

## Användbara metoder på audio-objektet

|method|desc|
|---|---|
|play()|startar ljudfilen|
|pause()|pausar ljudfilen | 

```js
let el = document.querySelector('audio');

el.play() // untz untz untz
```

## Användbara event från audio-objektet
|event|desc|
|---|---|
|timeUpdate|triggas vid varje ändring i tid vid spelning|
|ended|triggas när ljudfilen är slut|

```js
let el = document.querySelector('audio');

el.addEventListener('ended', (e) => {
    // handle event
}) 
```

![screen](https://user-images.githubusercontent.com/54267140/99225142-ddf9db00-27e7-11eb-8506-66ba919f28be.png)