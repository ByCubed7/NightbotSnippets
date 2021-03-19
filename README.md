# Commands Snippets <small>n bits'n'bops</small>
> Note: I'm experienced in programming but quite new to JS (and GitHub), so let me know if there's any inefficiencies, bugs, or all round improvements in general!

Note: There's a Nightbot limitation of 500 max characters and a script execution timeout of 25ms in a custom command.


Helpful Links:
[Nightbot Docs](https://docs.nightbot.tv/),
[javascript-minifier](https://javascript-minifier.com/)


<br><br>

## Contents:
- Codes
  - DnD-like Dice
- Grabbing code from other sources (eg pastebin)
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
!addcom !dice $(eval const q=decodeURIComponent("$(querystring)");let dice=""!==q?q:q.split(" ")[0];""==dice&&(dice="1d6"),p=dice.split("d");var amount=p[0],value=p[1],addit=0;dice.includes("+")&&(p=va.split("+"),value=p[0],addit=p[1]),amount=parseInt(amount),value=parseInt(value);var score=addit=parseInt(addit);for(i=0;i<amount;i++)score+=Math.ceil(Math.random()*value);`🎲 You rolled ${d} and scored ${sc} 🎲`)
```

##### Readable Code
```js
const q = decodeURIComponent(`$(querystring)`);

let dice = q !== '' ? q : q.split(" ")[0];
if (dice == "") dice = "1d6";

p = dice.split("d");
var amount = p[0];
var value = p[1];
var addit = 0;

if (dice.includes("+")) {
  p = va.split("+");
  value = p[0];
  addit = p[1];
};

// Cast to integers
amount = parseInt(amount);
value = parseInt(value);
addit = parseInt(addit);

// Add the initial addition
var score = addit;

for (i = 0; i < amount; i++)
  // Roll each dice and add it to score
  score += Math.ceil(Math.random() * value);

console.log(`🎲 You rolled ${dice} and scored ${score} 🎲`)
```

## Follow age
Also checkout [2g.be](https://2g.be/) and [this post](https://community.nightdev.com/t/followage-howlong-command-howlong-has-suddenly-stop-working/8751/2) for formats and other examples
```
!followage $(urlfetch https://api.2g.be/twitch/followage/$(channel)/$(touser)?format=ymwdhis)
```


## Shoutouts

```
!addcom !so Go check out $(touser)!! They were last playing $(twitch game $(touser)) <3
```
`$(twitch game $(touser))` == `$(twitch $(touser) "{{game}}")`


## Hug

```
!addcom !hug $(user) gave $(touser) a loving squeeze <3
```

## Bop
Bops a user
```
!addcom !bop BOP $(user) bopped $(touser) with a $(eval ["no horny stick","golf club","gladiators club","ironstar mace","gnome hooked hammer"][Math.floor(Math.random()*6)];), dealing $(eval Math.floor(Math.random()*100);) damage BOP
```
Chooses a random weapon from a list and damage to bop the user with.


## Grabbing code from other sources (eg pastebin)


```
!addcom !prophecy $(eval const user=`$(user)`; $(urlfetch json https://pastebin.com/raw/RuX9DEk5 ); `${j}`)
```
> Note: This took like 4 hours to get working lmao ;-;


---

> <small> Big secret thx to [Sabeden](discord.gg/majkuH4) for inspiring me to start this, great content creator and friend so go check him out :3 </small>
