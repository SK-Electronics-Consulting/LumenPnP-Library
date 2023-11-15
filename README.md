# LumenPnP-Library

This repo is to capture the resources, thoughts, data, and experiments related to using the [LumenPnP](https://www.opulo.io/products/lumenpnp) (or really any Pick and Place) in a small engineering shop.  

## Background

I'm an electrical engineer who spent over a year in industry.  A couple years ago, I started doing consulting.  As an electrical engineer consultant, I'm building boards pretty often.  My clients obviously wants better, faster, and cheaper, and it's my prerogative to balance that.  Better in this case a PCBA which is closer to their final product, so it would use small components.  Faster is pretty straightforward, but many of them balk at the typically 5 week lead times for most assembly houses.  Cheaper is also pretty straight forward, as they're either paying the CM or for my hours. 

## Premise

A pick and place is a manufacturing tool, and up until recently the capital investment has only made sense for CMs for which this is their primary business.  In recent years, various projects have started lowering the cost to make it more accessible to mid-scale manufacturing.  In both cases, the time of setting up the pick and place is amortized across a large or medium quantity of the same PCB, or the cost is reflected in a large NRE.  

The question rattling around my head is:  Can that setup time be amortized across a variety of boards, each with a quantity of 1, to provide the faster turn around time for my clients while not charging them my hourly rate?

## Assumptions

1. The PnP will not place all components.  It will just reduce the number of hand placements.
1. The machine and setup will not deteriorate between runs, which could be weeks to months.  For example, a Prusa 3d printer will sit happily for months until you need it again, assuming you removed the filament and stored it in a drybox.  But that removal and replacement process is only a few minutes and quite reliable.
1. Electronics design decisions will be made to facilitate the use of the PnP.  For Example:
    1. When practical, replace non-feedered passives with values that are in feeders already.  Ex: Using two 1k resistors instead of a 2.2k for I2C pull ups.  Using two 1uF caps instead of a 2uF cap.  Etc.
    1. Sticking with the MCUs that are available in the feeders.
    1. Selecting a NMOS+PMOS combo package instead of just an NMOS or PMOS.  

## Caveats

1. This approach won't apply to boards that are outside the capabilities of your PnP.  For the LumenPnP, this means 0201 and smaller passives.

## Open Questions

1. How many components can I cover with the least number of feeders?
1. What is the break-even point in terms of setup time vs manual placement?
1. How to bill for this service?  Aka, what does machine time cost?
1. Will it make sense to load all the unique parts so that the PnP will place the all or almost all the components?  This would require tracking how much time loading each slot requires.

## What to find in this repo

1. A library of KiCAD parts which are ready to go for use with the Pick and Place. This will include meta-data within each part to facilitate importing into OpenPnP.  
1. Data gathered about how effective this plan actually is.  For example, a [spreadsheet tracking my own builds](https://docs.google.com/spreadsheets/d/17FbHCPNZ1fRXliRPgTtyA1XI38gV4tv1DgYWPC0j7IY/edit?usp=sharing).
1. Any other files that could be helpful in making this decision for yourself.
