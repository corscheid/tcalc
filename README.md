# tcalc
A simple time calculator that can add and subtract time

## Usage

```
tcalc -<a|s> <HHMMSS> <HHMMSS>
```

## Arguments

`-a` : add two times together

`-s` : subtract the second time from the first time

`<HHMMSS>` : time or amount of time

```
Colons (:) are optional.
7 or more digit number arguments are not supported.
6-digit number arguments will be treated as HH:MM:SS
5-digit number arguments will be treated as 0H:MM:SS
4-digit number arguments will be treated as HH:MM:00
3-digit number arguments will be treated as 0H:MM:00
2-digit number arguments will be treated as 00:MM:00
1-digit number arguments will be treated as 00:0M:00
less than 1-digit number arguments are not supported.
```

## Add time

```
# add 18 mins 13 secs to 14:17:25
tcalc -a 14:17:25 00:18:13

# what time will it be in 35 mins if it's now 15:29?
tcalc -a 1529 35

# add 19 mins to 37 mins
tcalc -a 37 19

# add 1 hour 35 mins to 00:18:21 or 18 mins 21 secs
tcalc -a 001821 0135
```

## Subtract time

```
# how much time remains until 19:00 if it's now 14:38?
tcalc -s 19:00 14:38

# what time was it 45 minutes ago if it's now 19:27:25?
tcalc -s 19:27:25 45

# subtract 14 hours 45 mins from 23:39:00
tcalc -s 233900 144500
```

## Tips & Tricks

It may convenient to add these functions to your `.bashrc` or `.zshrc`

```
function NOW() {
	date +%H%M%S
}
function atcalc() {
	tcalc -a `NOW` $1
}
function ratcalc() {
	tcalc -a $1 `NOW`
}
function stcalc() {
	tcalc -s `NOW` $1
}
function rstcalc() {
	tcalc -s $1 `NOW`
}
```
Then, using current time is much easier than typing it in:
```
# what time is it in 45 minutes from now?
atcalc 45

# how about in 3 and a half hours from now?
atcalc 330

# what time is it in 13 hours from now?
atcalc 1300
```
ratcalc has the exact same results as atcalc, so it's basically just an alias
```
# what time was it 45 minutes ago?
stcalc 45

# what time was it 13 hours and 37 minutes ago?
stcalc 1337

# how much time remains between right now and 22:30?
rstcalc 2230

# how much time remains before midnight?
rstcalc 0
```
