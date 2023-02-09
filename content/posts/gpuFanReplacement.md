---
title: "GPU fan replacement"
date: 2022-04-25T18:03:13Z
showTitle: false
draft: false
toc: false
images:
tags: [
"hardware"
]
---
# GPU Fan Replacement
## Preface
The radeon R9 390 maybe an outdated card but still manages to keep up with 
competitors (for my use). My needs are limited so I don't want to fork out £500+ on a 
new card, so when I started to have overheating problems I was concerned. I realised
that the fans would only start when at 70°C and only one of the fans was operational. I 
was concerned. I first tried to see if it was a driver problem, so played around with older 
and newer drivers for a bit. To no avail I figured out that it was the fan itself. The fan 
would operate when set to 5000+ rpm but would only work on one card as before, and 
said the output was 3000 rpm. I also discovered it is a common issue with the xfx model, 
so ordered a replacement fan.

{{<image src="/images/gpu/gpuFirstImage.jpg" alt="XFX R9 390 before replacement" position="center" style="width: 80%">}}

## Installation of fan
You start off with voiding the waranty since the unfortunate part of this is that once you
open the card you void the warranty. Since my card had already gone past it's warranty I 
did not mind doing this. 

{{<image src="/images/gpu/gpuSecondImage.jpg" alt="Graphics card taken apart" position="center" style="width: 80%">}}

Whilst I had the card open I decided to get a good clean of it and replace the thermal 
paste. This will probably make a couple degrees different but nothing majorly. I cannot
measure this since I could not get a clear measurement before because the issues with 
the fans

{{<image src="/images/gpu/gpuThirdImage.jpg" alt="Replacing the fan on the heatsink" position="center" style="width: 80%">}}

After being stripped and cleaned I screwed the fans back into place and cable tied them
to the heatsink. This took three times because I somehow managed to put it upside down
three times but once I eventually got it right I plugged the new fan into the fan controller
and then put the screws back into place.

{{<image src="/images/gpu/gpuFinal.jpg" alt="Graphics card put together" position="center" style="width: 80%">}}

### Summary

The process of replacing a fan on a graphics card is simple as plug and play. By 
replacing the fans I saved a significant amount of money and now have quieter card. The 
temperatures idle around 34°C's compared to the 40-50 before hand, this also saves a
bit of electricity but nothing crazy. Not long after I done the replacement I managed to
get hold of an RX 6660 XT for not much off a friend. The R9 390 is now currently in
another machine that I plan on setting up as a homeserver.
