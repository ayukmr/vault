# wacc cld
![[wacc.png]]
I wanted to model this CLD in a spreadsheet, focusing on the WACC.

First, I collected constants. From the $\text{cost of debt}$ equation, I added $k$ and $\beta$, with $k$ as the starting interest rate, and $\beta$ as how much it increases given the debt ratio. I added the $\text{cost of equity}$ itself, since it's not in a loop, so nothing can affect it within the chosen section of the system. I also added two new constants: $\text{debt c}$ and $\text{equity c}$ ($\text{c}$ creatively standing for "constant"), the money given out to lenders/shareholders for the respective investment type. These are used because there weren't any equations given for $\text{equity amount}$ and $\text{debt amount}$, but both interact with the WACC indirectly, so I gave them both equations resembling $\text{c} / \text{cost}$. The $\text{equity amount}$ is given as a sort of second-stage constant, since it only relies on two constants with the formula $\text{equity c}/\text{cost of equity}$.

Then, I added columns for the things that would change during evaluation. $\text{x}$, the ratio of debt to equity, is $\text{debt amount}/\text{equity amount}$. $\text{cost of debt}$ is $k(1 + x)^\beta$, and $\text{debt amount}$ is $\text{debt c}/\text{cost of debt}$. Finally, the WACC is given as $\frac{1}{1 + x} (\text{cost of equity}) + \frac{x}{1 + x} (\text{cost of debt})$. The equation initially didn't make a lot of sense, but expanding it makes it much more clear. $\frac{1}{1 + x} = \frac{1}{1 + d/e} = \frac{1}{(e + d)/e} = \frac{e}{e + d}$, and similarly, $\frac{x}{1 + x} = \frac{d/e}{1 + d/e} = \frac{d/e}{(e + d)/e} = \frac{d}{e + d}$.

"Running" the iteration cycle was just copying each row of the spreadsheet down, where it depends on the previous row's calculations. It seems to converge relatively quickly, like in the screenshot below.

![[wacc-sheet.png]]
