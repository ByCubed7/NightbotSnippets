# Commands Snippets <small>n bits'n'bops</small>
> Note: I'm experienced in programming but quite new to JS (and GitHub), so let me know if there's any inefficiencies, bugs, or all round improvements in general!

There's a Nightbot limitation of 500 max characters and a script execution timeout of 25ms in a custom command.

Helpful Links:
[Nightbot Docs](https://docs.nightbot.tv/),
[javascript-minifier](https://javascript-minifier.com/)

<br>

## Contents:
- Dice
- Follow age
- Shoutouts
- Hug
- Bop
- Prophecy
- Death / Horny-jail counter
- Multi

---



## Dice
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

// Parse to integers
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
Shouts out a user in chat
```
!addcom !so Go check out $(touser) at https://www.twitch.tv/$(touser)!! They were last playing $(twitch game $(touser)) <3
```
`$(twitch game $(touser))` == `$(twitch $(touser) "{{game}}")`



## Hug
```
!addcom !hug $(user) gave $(touser) a loving squeeze <3
```



## Bop
Bops a user with a random weapon from a list, with a random amount of damage.

##### Usage
!bop [user] <br>
!bop ChessyGrill
  
##### Returns
`ByCubed7 bopped ChessyGrill with a undefined, dealing 20 damage BOP`

##### Addcom
```
!addcom !bop BOP $(user) bopped $(touser) with a $(eval const responses = ["no horny stick","golf club","gladiators club","ironstar mace","gnome hooked hammer"]; responses[Math.floor(Math.random() * responses.length)];) dealing $(eval Math.floor(Math.random() * 100);) damage BOP
```

##### Readable Code
```js
[
  "no horny stick",
  "golf club",
  "gladiators club",
  "ironstar mace",
  "gnome hooked hammer"
][Math.floor( Math.random()*4 )];
)

Math.floor( Math.random()*100 );
```


## Prophecy
This example grabs and runs some code from pastebin

##### Usage
!prophecy <user>

##### Returns
`In the first Jurassic Park movie, the Tyrannosaurus Rex wasn't chasing the jeep. ByCubed7 was chasing the Tyrannosaurus AND the jeep.`

##### Addcom
```
!addcom !prophecy $(eval const user=`$(touser)`; $(urlfetch json https://pastebin.com/raw/RuX9DEk5 ); `${j}`)
```
> Note: This took like 4 hours to get working lmao ;-;



## 8ball

##### Usage
!8ball Will I ever be loved?
  
##### Responce
`All signs point to yes...`

##### Addcom
```
!addcom !8ball 🎱 $(eval const responses = ['All signs point to yes...', 'Yes!', 'My sources say nope.', 'You may rely on it.', 'Concentrate and ask again...', 'Outlook not so good...', 'It is decidedly so!', 'Better not tell you.', 'Very doubtful.', 'Yes - Definitely!', 'It is certain!', 'Most likely.', 'Ask again later.', 'No!', 'Outlook good.', 'Don\'t count on it.']; responses[Math.floor(Math.random() * responses.length)];)
```

##### Readable Code
```js
const responses = [
'Yes - Definitely!', 
'Yes!', 
'All signs point to yes...', 
'It is decidedly so!', 
'It is certain!', 
'Most likely.', 
'Outlook good.', 
'You may rely on it.', 
'Ask again later.',
'Concentrate and ask again...', 
'Better not tell you.', 
'Outlook not so good...', 
'Don\'t count on it.',
'Very doubtful.', 
'My sources say nope.', 
'No!'
]; 

console.log(responses[Math.floor(Math.random() * responses.length)]);
```



## Uptime

##### Usage
!Uptime

##### Responce
`Grayscaped has been up for 2 hours 14 minutes 41 seconds`

##### Addcom
```
!addcom !uptime $(channel) has been up for $(twitch $(channel) "{{uptimeLength}}")
```



## Death / Horny-jail counter

##### Usage
!dead <br>
!horny Grayscaped

##### Responce
`That's 24 deaths now!` <br>
`Nightbot sent Grayscaped to horny jail BOP . (24 people have been sent to horny jail)`

##### Addcom
```
!addcom !dead That's $(count) deaths now!
```
```
!addcom !horny /me sent $(touser) to horny jail BOP . ($(count) people have been sent to horny jail)
```



## Multi
##### Usage
!multi chrisanthemum

##### Responce
`https://www.multitwitch.tv/havenhand/chrisanthemum`

##### Addcom
```
!addcom !multi https://www.multitwitch.tv/$(channel)/$(1)
```

---
> <small> Big secret thx to [Sabeden](discord.gg/majkuH4) for inspiring me to start this, great content creator and friend so go check him out :3 </small>
