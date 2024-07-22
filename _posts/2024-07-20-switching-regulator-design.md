---
title: Tips for designing a switching regulator (feat. TI LMR51450)
tags: [Hardware, Electronics Design]
style: border
color: success
description: Provides essentials for designing a switching regulator, take the step-down DC/DC converter LMR51450 from Texas Instruments as an example.
---

In this post I'm going to share some useful tips when designing a switching regulator, together with the considerations of picking up proper regulator ICs and other components.

As Texas Instruments has a wide category of power regulators, I am going to use the buck down converter [LMR51450](https://www.ti.com/lit/ds/symlink/lmr51440.pdf) as an example. The general rules can be applied to most of other switching regulators.

## Selection of a proper regulator IC

---

The first thing is to note down the power requirements of your design, this should be done prior to looking for regulator ICs. Normally, the key considerations are input voltage, output voltage, output current, etc..

In this example, my design requirements are:

- Input voltage `V_IN`: from 20V to 30V, with a nominal voltage of 24V.
- Output voltage `V_OUT`: 5V fixed.
- Output current `I_OUT`: from 2A to 5A.
- Efficiency: > 90%.
- Other: for compact design, low-cost, built-in protection ...

Depending on the above requirements, we can apply this as filters for components selection in Digi-key or Mouser to find suitable regulator ICs. However, if we just want to use products from Texas Instruments, we can use the [WEBENCH POWER DESIGNER](https://webench.ti.com/power-designer/) to quickly find the appropriate ICs from TI.

After giving my input in the _WEBENCH_ designer, I quickly get the solutions from TI, I finally pick the LMR51450 as my solution.

{% include elements/figure.html image="/assets/images/2024-07-20/webench_designer_tool.png" caption="WEBENCH POWER DESIGNER" %}

## Application circuit of LMR51450

---

The typical application circuit diagram for LMR51450 is shown below:

{% include elements/figure.html image="/assets/images/2024-07-20/application_circuit.png" caption="Application Circuit" %}

The detailed design procedure is described based on the above circuit.

### Set the output voltage

The output voltage of LMR51450 is adjustable through the resistor divider on pin `FB`.

$$
R_{FBT} = \frac{(V_{OUT}-V_{REF})}{V_{REF}} \times R_{FBB}
$$

where $$V_{REF} = 0.8V$$ to the datasheet.

To set the output voltage to 5V, choose $$R_{FBe}=100k\Omega$$ and $$R_{FBB}=19.2k\Omega$$.
