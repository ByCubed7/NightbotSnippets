# Commands Snippets <small>n bits'n'bops</small>
> Note: I'm experienced in programming but quite new to JS (and GitHub), so let me know if there's any inefficiencies, bugs, or all round improvements in general!

Note: There's a Nightbot limitation of 500 max characters in a custom command



## Contents:
- Codes
  - DnD-like Dice
- Shoutouts
---

### DnD-like Dice
Roles a dice similar to those used in Dungeons and Dragons 5e (defaults to one 6 sided dice).


##### Usage
!dice [dice string] <br>
!dice 1d20

###### Returns
`🎲 You rolled 1d20 and scored 18 🎲`

##### !addcom
```
!addcom !dice $(eval const q=decodeURIComponent(`$(querystring)`);let d=q!==''?"1d6":`$(query)`;d=d.split(" ")[0];if(d=="")d="1d6";p=d.split("d");var am=p[0];var va=p[1];var ad=0;if(d.includes("+")){p=va.split("+");va=p[0];ad=p[1]};am=parseInt(am);va=parseInt(va);ad=parseInt(ad);var sc=ad;for(i=0;i<am;i++)sc+=Math.ceil(Math.random()*va);`🎲 You rolled ${d} and scored ${sc} 🎲`)
```

##### Readable Code
```js
const q = decodeURIComponent(`$(querystring)`);

let dice = q !== '' ? "1d6" : `$(query)`;
dice = dice.split(" ")[0];
if (dice == "") dice = "1d6";

p = dice.split("d");
var amount = p[0];
var value = p[1];
var addit = 0;

if (d.includes("+")) {
  p = va.split("+");
  value = p[0];
  addit = p[1];
};

amount = parseInt(am);
value = parseInt(value);
addit = parseInt(ad);

var score = addit;
for (i = 0; i < amount; i++)
  score += Math.ceil(Math.random() * value
);

`🎲 You rolled ${dice} and scored ${score} 🎲`
```


---

> <small> Big secret thx to [Sabeden](discord.gg/majkuH4) for inspiring me to start this, great content creator and friend so go check him out :3 </small>
