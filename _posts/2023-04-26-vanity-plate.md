---
layout: post
title: "How To Find A Short Vanity Plate in Florida"
subtitle: "Using Python to find every short vanity plate combination available in Florida."
tags: "python florida project bruteforce scrape web"
---
In the UK, short license plates are worth their weight in gold - literally, some [examples](https://www.swiftreg.co.uk/blog/10-most-expensive-private-number-plates-ever-sold) have sold upwards of £500,000. As a result, it was only fitting that I should take advantage of the relatively low adoption rate of vanity plates in Florida to procure a unique and very short plate: **RP**

When I first decided I wanted a vanity plate, my primary goal was to find one that was as short as possible. To help me, I developed a small Python module called [FloridaPlateScraper](https://github.com/reecepounder/FloridaPlateScraper) that tests every single possible permutation of the alphanumericals with the DMV's website, and saves any that are available.

To use it, download and import the [dmv_check.py](https://downgit.github.io/#/home?url=https://github.com/reecepounder/FloridaPlateScraper/blob/main/dmv_check.py) file and run the check function with the legnth you would like to test for. 

The program automatically runs through every combination of letters and numbers and produces the available combinations in a file called `x_letters_0000000.json` (epoch time appended), which you can then process futher. You could also redirect the output to a different program if you chose to, by setting `returnValues=True`. Here's an example:

```python
import dmv_check
# Check for all 3 letter permutations and make a file with the results
dmv_check.check()

# ... or you can use the returnValues parameter to return the results as a list instead
availablePlates = dmv_check(3,returnValues=True)
print(availablePlates)

# ... You can also toggle output to console (defaults to __debug__ unless overridden).
dmv_check(3, printDebugStatements=False)
```

This basically just sends POST requests to the online DMV portal for checking plates. There are some weird parameters that have to be passed along in form data and headers, but all of that is included. It processes the response page to interpret whether the plate is available or not. Pretty simple.

## Current availability
When I first built this on October 27, 2020, there were 20 Florida 2-letter license plates (not including with numbers). As of writing (April 26, 2023) there are exactly 0 left. In 2020, there were 8091 3-letter plates, but I am unsure how many still exist. Try it, and find out for yourself.



The reason so many short vanity plates are gone is largely due to the surge of TikTok people wanting license plate. In particular, a user named [urplateplug](https://tiktok.com/@urplateplug) has been advertising this service for many other states as well as Florida. I think it is ridiculous to charge $100 for him to give you a list of all 2 letter plates. If you live in Florida, spend the 20 minutes it would take you to figure out how to run Python code and use this instead - please.

Maybe it would be fun to tackle those states and launch a small website that updates daily, maybe save people some cash. That could be a fun project - I guess you'll know if you follow my [LinkedIn](https://linkedin.com/in/reecepounder).

## Closing thoughts

I also got RP3 - the reason being that, by the time I went to register another plate, RP0-2 were already taken  - I got my original one just in time.

It would probably be a good idea for the Florida DMV to rate limit the form, even slightly, to reduce server load from scans like this. Alternatively you could also just submit a public records request for the information, but this is a fun thought experiment.

I thought it would be a good idea to rename the project from FloridaLicensePlateBruteforcer as that seemed a bit harsh. Though, it's a pretty apt description of what bruteforcing actually is.

As a side note on license plates, I am absolutely infuriated by the (presumably) teenager who registered the vanity plate "40 RA" on his Ford Mustang V6. If you want to know why that plate is important, click [here](https://jalopnik.com/an-amazing-lotus-tuned-sedan-terrorized-the-uk-in-a-vio-1575033146). If I could have any plate in the entire world, I would get this one, so that one day I can register it to my very own Lotus Carlton and confuse the living daylight out of people online. Tee hee.

## Future modifications
The program is archived. I have no interest in continued development. If I did, I would only need to update to match Florida DMV updates or add multithreading. But the performance is acceptable for me for now. If using this in your own project, I would strongly recommend using it asynchronously as it takes 129 seconds for 1296 checks (2 letters) and much longer the larger you go.

