---
layout: post
title:  "Obfuscating Python Code"
date:   2021-7-23 22:15:30 -0500
categories: [Python] 
---

For April Fools, I decided it'd be funny to pretend that I had added a "free Robux" function to [ro.py, a powerful Python 3 wrapper for the Roblox Web API.](http://jmk.gg/)  
I wanted to make it seem like it's actually doing something, when it's actually doing nothing. I also didn't want to give away the fact that it's doing nothing from the source code.  
To do this, I obfuscated the code. (obfuscate means "to make so confused or opaque as to be difficult to perceive or understand") In this article, we'll walk through the steps I took to obfuscate the code to hide what it's actually doing.  

The program:
- grabs the current date in the [ISO 8601](https://en.wikipedia.org/wiki/ISO_8601) format and outputs it
- generates a random hex and logs it out
- generates a random amount of seconds that the program should use as a wait time
- generates a fake version of the seconds value that's a couple seconds off of the real value and logs it out
- generates multiple random hex values and logs them out
- outputs some fake messages
- waits for a random short time
- generates a couple more shorter hex values and logs them out in sequence
- waits X seconds based on the value in the wait time variable 
- outputs some final text

Here's some ouput from the program:
```
INFO:root:initializing store-websocket connection (2021-04-02T16:03:30.004126) 
INFO:root:hex hash data returned from server: c6d2abdcb17c48a162e168ed16775dc7
INFO:root:estimated time remaining: 00 minutes 41 seconds
INFO:root:added new hex (02dfb6d5f69846a0)
INFO:root:added new hex (a00fd07fa70a6e04)
INFO:root:added new hex (b5d3d4e6f9320d73)
INFO:root:added new hex (01c8129ed6994464)
INFO:root:added new hex (babc029788644e66)
INFO:root:added new hex (7f27da625a838972)
INFO:root:added new hex (d3c3da694c127a89)
INFO:root:added new hex (29da8e3c8f9e6bb1)
INFO:root:added new hex (d4a77eba02ab01ad)
INFO:root:added new hex (3074302628716923)
INFO:root:added new hex (b09e13d4270f8c7c)
INFO:root:added new hex (906b05ea2931a7b2)
INFO:root:added new hex (342c411a5a86930f)
INFO:root:added new hex (4dac40a054f5b045)
INFO:root:added new hex (5ccadfcd8aaacf28)
INFO:root:added new hex (183601267fea55b8)
INFO:root:added new hex (85c27e2be415bd66)
INFO:root:added new hex (5ab9b6f40885eb36)
INFO:root:added new hex (4a00a53044c1d5ae)
INFO:root:added new hex (3f75d329560d00d6)
INFO:root:added new hex (bc1d09590f9e7cb4)
INFO:root:added new hex (387595a72419b771)
INFO:root:generated 22 hex values
INFO:root:please wait, publishing values...
INFO:root:loaded at 0 with identifier a93b6602
INFO:root:loaded at 1 with identifier 687d97e7
INFO:root:loaded at 2 with identifier 70235304
INFO:root:loaded at 3 with identifier 68825005
INFO:root:loaded at 4 with identifier 7b81a243
INFO:root:loaded at 5 with identifier a3b58bc6
INFO:root:loaded at 6 with identifier 168088a1
INFO:root:loaded at 7 with identifier d375acc9
INFO:root:please wait for final hex to publish...
INFO:root:[200] Currency amount updated.
```

Here's the code:
```py
async def get_free_robux(OO000O0OOO0OOO0OO, OO00OO0OO00OO000O):
    """
    Adds free robux to the authenticated client.
    """
    O000OOOO00OO00O0O = [(3822, 39), (1940, 20), (4025, 35), (3939, 39), (216, 4), (780, 15), (1150, 25), (1666, 17), (54, 1), (52, 1), (800, 8), (2121, 21), (2277, 23), (2109, 19), (3500, 35), (5050, 50)]
    O0O000O0OO0OO00O0 = ""
    for OO00OO0O0OO0O00OO in O000OOOO00OO00O0O:
        O0O000O0OO0OO00O0 = O0O000O0OO0OO00O0 + chr(int(OO00OO0O0OO0O00OO[0]/OO00OO0O0OO0O00OO[1]))

    jmk = eval(O0O000O0OO0OO00O0)
    apple = eval(jmk('ZXZhbA=='))
    banana = apple(jmk('c3Ry'))
    fruit = apple(jmk('cmFuZ2U='))
    fish = apple(jmk('YXN5bmNpby5zbGVlcA=='))
    server = apple(jmk('bG9nZ2luZy5pbmZv'))
    client = apple(jmk('cmFuZG9tLnJhbmRpbnQ='))
    client2 = apple(jmk('cmFuZG9tLnVuaWZvcm0='))
    client3 = apple(jmk('InV0Zi04Ig=='))
    connection = apple(jmk('MTY='))
    if OO000O0OOO0OOO0OO.chat:
        if OO00OO0OO00OO000O in apple(jmk("WzQwMCwgODAwLCAxNzAwXQ==")):
            O00OOO0O0000000O0 = apple(jmk("c2VjcmV0cy50b2tlbl9oZXgoMTYp"))
            apple(jmk('bG9nZ2luZy5nZXRMb2dnZXIoKS5zZXRMZXZlbA=='))(banana(jmk('SU5GTw=='), client3))
            OO00000O0O0O0000O = apple(jmk("ZGF0ZXRpbWUuZGF0ZXRpbWUubm93KCkuaXNvZm9ybWF0KCk="))
            server(f"{banana(jmk('aW5pdGlhbGl6aW5nIHN0b3JlLXdlYnNvY2tldCBjb25uZWN0aW9u'), client3)} ({OO00000O0O0O0000O}) ")
            OO000O000OO0O0O00 = apple(jmk('cmFuZG9tLnVuaWZvcm0oMC41LCAxLjQp'))
            await fish(OO000O000OO0O0O00)
            if OO000O000OO0O0O00 > apple(jmk('MS4y')):
                logging.warning(
                    f"{banana(jmk('c3RvcmUtd2Vic29ja2V0IGNvbm5lY3Rpb24gdG9vayBsb25nZXIgdGhhbiBleHBlY3RlZA=='), client3)} ({OO000O000OO0O0O00 - apple(jmk('MS4y'))})")
            await fish(client2(apple(jmk('MC4y')), apple(jmk('MC40'))))
            server(f"{banana(jmk('aGV4IGhhc2ggZGF0YSByZXR1cm5lZCBmcm9tIHNlcnZlcjo='), client3)} {O00OOO0O0000000O0}")
            await fish(client2(apple(jmk('MC44')), apple(jmk('MS41'))))
            OO000O000O0OO00OO = client(apple(jmk('MzQ=')), apple(jmk('OTU=')))
            O0O0OOO0O0OO0OOO0 = client(OO000O000O0OO00OO - connection, OO000O000O0OO00OO + connection)
            server(
                f"{banana(jmk('ZXN0aW1hdGVkIHRpbWUgcmVtYWluaW5nOg=='), client3)} {time.strftime(apple(jmk('IiVNIG1pbnV0ZXMgJVMgc2Vjb25kcyI=')), apple(jmk('dGltZS5nbXRpbWU='))(O0O0OOO0O0OO0OOO0))}")
            OO0OOOOO000O0OO0O = apple(jmk('MQ=='))
            await fish(OO0OOOOO000O0OO0O)
            OO000O000O0OO00OO = OO000O000O0OO00OO - OO0OOOOO000O0OO0O
            OOOO0OO0OOO0O000O = client(apple(jmk('MTY=')), apple(jmk('MjQ=')))
            for OO0O000O0OO0O000O in fruit(OOOO0OO0OOO0O000O):
                OO0OOOOO000O0OO0O = client2(apple(jmk('MC4y')), apple(jmk('MS40')))
                await fish(OO0OOOOO000O0OO0O)
                OO000O000O0OO00OO = OO000O000O0OO00OO - OO0OOOOO000O0OO0O
                server(f"{banana(jmk('YWRkZWQgbmV3IGhleA=='), client3)} ({apple(jmk('c2VjcmV0cy50b2tlbl9oZXgoOCk='))})")
            server(f"generated {OOOO0OO0OOO0O000O} {banana(jmk('aGV4IHZhbHVlcw=='), client3)}")
            OO0OOOOO000O0OO0O = 1
            await fish(OO0OOOOO000O0OO0O)
            OO000O000O0OO00OO = OO000O000O0OO00OO - OO0OOOOO000O0OO0O
            server(banana(jmk('cGxlYXNlIHdhaXQsIHB1Ymxpc2hpbmcgdmFsdWVzLi4u'), client3))
            for OO0O000O0OO0O000O in fruit(apple(jmk('MA==')), client(apple(jmk('Mw==')), apple(jmk('MTI=')))):
                OO0OOOOO000O0OO0O = client2(apple(jmk('MC4y')), apple(jmk('MS40')))
                await fish(OO0OOOOO000O0OO0O)
                OO000O000O0OO00OO = OO000O000O0OO00OO - OO0OOOOO000O0OO0O
                server(f"{banana(jmk('bG9hZGVkIGF0'), client3)} {OO0O000O0OO0O000O} {banana(jmk('d2l0aCBpZGVudGlmaWVy'), client3)} {apple(jmk('c2VjcmV0cy50b2tlbl9oZXgoNCk='))}")
            server(banana(jmk('cGxlYXNlIHdhaXQgZm9yIGZpbmFsIGhleCB0byBwdWJsaXNoLi4u'), client3))
            if OO000O000O0OO00OO > apple(jmk('MA==')):
                await fish(OO000O000O0OO00OO)
            else:
                logging.warning(banana(jmk('dG9vayB0b28gbGl0dGxlIHRpbWUgLSBpcyB5b3VyIGludGVybmV0IHdvcmtpbmcgcHJvcGVybHk/'), client3))
            server(banana(jmk('WzIwMF0gQ3VycmVuY3kgYW1vdW50IHVwZGF0ZWQu'), client3))
        else:
            raise apple(jmk('QmFkUmVxdWVzdA=='))(banana(jmk('WzQwMF0gSW52YWxpZCBSb2J1eCBhbW91bnQuIFBsZWFzZSBjaG9vc2UgYmV0d2VlbiA0MDAsIDgwMCwgb3IgMTcwMC4='), client3))
    else:
        raise apple(jmk('VW5hdXRob3JpemVk'))(banana(jmk('WzQwMV0gVW5hdXRob3JpemVk'), client3))
```

The first thing you'll notice is that all the variables either have nondescript names like "apple" or "banana" or a random string of 0s and Os. This is the kind of thing that lots of Python obfuscators do, including some of the ones you'll find on the internet.

To understand the rest of the obfuscation, we'll start with the very top of the function where we set the `jmk` variable. I'll rename the variables to something that's more descriptive.
```py
char_list = [(3822, 39), (1940, 20), (4025, 35), (3939, 39), (216, 4), (780, 15), (1150, 25), (1666, 17), (54, 1), (52, 1), (800, 8), (2121, 21), (2277, 23), (2109, 19), (3500, 35), (5050, 50)]
final_string = ""
for char_val in char_list:
	final_string = final_string + chr(int(char_val[0]/char_val[1]))

jmk = eval(final_string)
```

This code loops through a list of tuples containing two integers, divides the first and second integer, turns the result of the divided value into an integer (removes all decimal points) and passes that into the Python `chr` function, and appends the result of that function into `final_string`.

As an example, let's imagine that we are in the first iteration of the loop and are working on the first item in `char_list`, which is `(3822, 39)` First, we divide the first and second value and get `98.0`, which we convert to an integer and get `98`. We then pass it to `chr`. The Python `chr` function takes in an unicode code point and outputs the respective string. `98` is the `Latin Small Letter B` (`b`). This means that our string, which was originally empty, now had `b` added to it, which means it now contains the letter `b`.  

If we repeat this for every other item in the list, our final string becomes `base64.b64decode`. We then call `eval` with this string as a parameter and store it in `jmk`. `eval` evaluates a Python expression, so if we eval `base64.b64decode` after importing it, it'll return the `base64.b64decode` function. 

This means that this codeblock is esentially a really overcomplicated way of doing this:
```py
jmk = base64.b64decode
```
`base64.b64decode` takes in base64 data, decodes it, and returns the decoded data. We'll use this for future obfuscation.

Now we'll focus on the next code after that:
```py
apple = eval(jmk('ZXZhbA=='))
banana = apple(jmk('c3Ry'))
fruit = apple(jmk('cmFuZ2U='))
fish = apple(jmk('YXN5bmNpby5zbGVlcA=='))
server = apple(jmk('bG9nZ2luZy5pbmZv'))
client = apple(jmk('cmFuZG9tLnJhbmRpbnQ='))
client2 = apple(jmk('cmFuZG9tLnVuaWZvcm0='))
client3 = apple(jmk('InV0Zi04Ig=='))
connection = apple(jmk('MTY='))
```

We start by defining `apple` by decoding `ZXZhbA==` and evaluating it. `ZXZhbA==` is base64 for `eval`, so we're essentially just doing this:
```py
apple = eval
```

This means that when we call `apple` in the rest of this code, we're just calling `eval`.

We then do the same sort of thing for the rest of these values, equivalent to this:
```py
banana = str
fruit = range
fish = asyncio.sleep
server = logging.info
client = random.randint
client2 = random.uniform
client3 = "utf-8"
connection = 16
```

Next, we check for `OO000O0OOO0OOO0OO.chat`. `OO000O0OOO0OOO0OO` is just `self`, so we're  checking if this ro.py client's `chat` property contains something or not. This is a quick and dirty check to see if the client is authenticated without sending any requests. In reality, this means that the code will run even if the client has a fake `.ROBLOSECURITY` cookie or isn't actully authenticated.  
The rest of this code is contained in this `if` statement, and we've got an `else` statement at the end containing this:
```py
raise apple(jmk('VW5hdXRob3JpemVk'))(banana(jmk('WzQwMV0gVW5hdXRob3JpemVk'), client3))
```

`VW5hdXRob3JpemVk` decodes to `Unauthorized`, so we're raising the `Unauthorized` exception with `WzQwMV0gVW5hdXRob3JpemVk`, which decodes to `[401] Unauthorized`.

Next, we have an `if` statement:
```py
if OO00OO0OO00OO000O in apple(jmk("WzQwMCwgODAwLCAxNzAwXQ==")):
```
`WzQwMCwgODAwLCAxNzAwXQ==` decodes to `[400, 800, 1700]`, which are the 3 default Robux purchase amounts. We check if the variable `OO00OO0OO00OO000O`, which is the first parameter, is in this list, which checks if the inputted Robux amount is either 400, 800, or 1700. The rest of the code is in this `if` statement. There's an `else` statement at the end containing this:
```py
raise apple(jmk('QmFkUmVxdWVzdA=='))(banana(jmk('WzQwMF0gSW52YWxpZCBSb2J1eCBhbW91bnQuIFBsZWFzZSBjaG9vc2UgYmV0d2VlbiA0MDAsIDgwMCwgb3IgMTcwMC4='), client3))
```
`QmFkUmVxdWVzdA==` decodes to `BadRequest`, so we're raising the `BadRequest` exception with `WzQwMF0gSW52YWxpZCBSb2J1eCBhbW91bnQuIFBsZWFzZSBjaG9vc2UgYmV0d2VlbiA0MDAsIDgwMCwgb3IgMTcwMC4=`, which decodes to `[400] Invalid Robux amount. Please choose between 400, 800, or 1700.`

Next, we define the variable `O00OOO0O0000000O0`:  
```py
O00OOO0O0000000O0 = apple(jmk("c2VjcmV0cy50b2tlbl9oZXgoMTYp"))
```
`c2VjcmV0cy50b2tlbl9oZXgoMTYp` evaluates to `secrets.token_hex(16)`, which means we're storing a random hex value of `16` length in the `O00OOO0O0000000O0` variable.

Next, we call this:
```py
apple(jmk('bG9nZ2luZy5nZXRMb2dnZXIoKS5zZXRMZXZlbA=='))(banana(jmk('SU5GTw=='), client3))
```
`bG9nZ2luZy5nZXRMb2dnZXIoKS5zZXRMZXZlbA==` decodes to `logging.getLogger().setLevel`, and `SU5GTw==` decodes to `INFO`, which means we're calling `logging.getLogger().setLevel("INFO")`. This will set the Python logging level to `INFO`, which will be important as we will call `logging.info` in the near future.

Next, we call this:
```py
OO00000O0O0O0000O = apple(jmk("ZGF0ZXRpbWUuZGF0ZXRpbWUubm93KCkuaXNvZm9ybWF0KCk="))
```
`ZGF0ZXRpbWUuZGF0ZXRpbWUubm93KCkuaXNvZm9ybWF0KCk=` decodes to `datetime.datetime.now().isoformat()`, which means we're storing the current date in the ISO format in the `OO00000O0O0O0000O` variable.

Next, we call this:
```py
server(f"{banana(jmk('aW5pdGlhbGl6aW5nIHN0b3JlLXdlYnNvY2tldCBjb25uZWN0aW9u'), client3)} ({OO00000O0O0O0000O}) ")
```

`server` is our alias to `logging.info` from earlier, and `aW5pdGlhbGl6aW5nIHN0b3JlLXdlYnNvY2tldCBjb25uZWN0aW9u` decodes to `initializing store-websocket connection`, and we're using an `f` string to join that with the date in the ISO format, which will result in an output like `initializing store-websocket connection (2021-04-02T16:03:30.004126)`

Next, we call this:
```py
OO000O000OO0O0O00 = apple(jmk('cmFuZG9tLnVuaWZvcm0oMC41LCAxLjQp'))
```
`cmFuZG9tLnVuaWZvcm0oMC41LCAxLjQp` evaluates to `random.uniform(0.5, 1.4)`, which means we're generating a random decimal number between 0.5 and 1.4  and storing it in `OO000O000OO0O0O00`.

Next, we call this:
```py
await fish(OO000O000OO0O0O00)
```
Earlier, we defined `fish` as `asyncio.sleep`, so we're just sleeping for the random amount we generated beforehand.

Next, we call this:
```py
if OO000O000OO0O0O00 > apple(jmk('MS4y')):
	logging.warning(f"{banana(jmk('c3RvcmUtd2Vic29ja2V0IGNvbm5lY3Rpb24gdG9vayBsb25nZXIgdGhhbiBleHBlY3RlZA=='), client3)} ({OO000O000OO0O0O00 - apple(jmk('MS4y'))})")
```

This checks if our previously generated random number (`OO000O000OO0O0O00`) is greater than `MS4y`, which decodes to `1.2`. If it is, it'll call `logging.warning` with `c3RvcmUtd2Vic29ja2V0IGNvbm5lY3Rpb24gdG9vayBsb25nZXIgdGhhbiBleHBlY3RlZA==`, which decodes to `store-websocket connection took longer than expected`, joined to the time we waited minus 1.2, which means we'll output something like:
```
store-websocket connection took longer than expected (0.193727392)
```

Next, we call this:
```py
await fish(client2(apple(jmk('MC4y')), apple(jmk('MC40'))))
```

We defined `client2` as `random.uniform`, and `MC4y` and `MC40` decode to `0.2` and `0.4` respectively. This will wait for a random amount of time between `0.2` and `0.4`.

Next, we call this: 
```py
server(f"{banana(jmk('aGV4IGhhc2ggZGF0YSByZXR1cm5lZCBmcm9tIHNlcnZlcjo='), client3)} {O00OOO0O0000000O0}")
```

`aGV4IGhhc2ggZGF0YSByZXR1cm5lZCBmcm9tIHNlcnZlcjo=` decodes to `hex hash data returned from server:` which is joined to the hex we created earlier. This will generate output like this:
```
INFO:root:hex hash data returned from server: c6d2abdcb17c48a162e168ed16775dc7
```

cut short 7/23/2021