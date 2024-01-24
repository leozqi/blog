+++
title="192.1 · Engineering economics"
date=2023-08-11
+++

ECE 192 teaches students how to compare projects using key metrics like the
_internal rate of return_ (IRR).
The Fall 2023 offering focuses on the analysis of large power generating plants.

Engineers must consider the use of _resources_, _labour_, _time_,
_environmental impact_, and _legal requirements_ when making project planning
decisions. We always select the project that accomplishes the primary objective
while providing the maximum _net benefit_, which we calculate using _cost
analysis_.

## Cost analysis

All costs can be classified as _fixed_ (constant throughout project lifetime) or
_variable_ (depending on the internal activity of the project). Their sum is
known as the _total cost_. 

$$TC = \sum FC + \sum VC$$

{% definition(ref="Sunk costs") %}
Sunk costs are costs due to a past decision. They should not be considered when
making any future decisions.
{% end %}

{% definition(ref="Opportunity cost") %}
An _opportunity cost_ is any potential net benefit that you could have received
if you made a mutually-exclusive decision to one you are currently considering.

For example, if you could do $A$ or $B$ and chose to do $B$, the opportunity
cost would be all the net benefit of doing $A$ subtracted by the net benefits of
doing $B$.
{% end %}

## Capital cost estimation

_Capital cost estimation_ is when we approximate single, large expenditures of a project.
We can do so using the _per-unit_, _segmenting_, or _power-sizing_ models.

{% definition(ref="Per-unit model") %}
We estimate the cost of a single unit. We then multiply this cost by an
estimation of the number of units needed.
{% end %}

{% definition(ref="Segmenting model") %}
We divide a project into a segmented timeline. The costs of each segment are
estimated and then added together.
{% end %}

{% definition(ref="Power-sizing model") %}
A model used to estimate the costs of industrial plants and equipment. We scale
"up" and "down" known costs to account for economies of scale. That is,
producing "more" of something usually results in lower average cost.

$$\frac{\text{Cost }A}{\text{Cost }B} = \left (\frac{\text{Size }A}{\text{Size
}B}\right )^\gamma$$

The exponent $\gamma$ is called the _power-sizing exponent_ and takes into
account economies of scale.

Note we must compare the sizes of $A$ and $B$ with the same unit and the costs
of $A$ and $B$ must be at the same point in time. This means that if $A$'s cost
was 10 years ago, we must use a cost index to accurately harmonize past prices
to today's value.

Analyzing projects with $\gamma$:

- If $\gamma=1$, costs grow linearly.
- If $\gamma < 1$, producing more results in lower average cost.
- If $\gamma > 1$, producing more results in higher average cost (diseconomy of
  scale)
{% end %}

For single expenditures, we may use historical cost data to estimate new cost values using _indices_.
Given a present cost $C(t)$ and historic cost $C(t_0)$, and present index value
$I(t)$ with historical value $I(t_0)$, we may say that:

$$C(t) = C(t_0)\cdot \frac{I(t)}{I(t_0)}$$

Indices usually only account for annual changes in prices.

### Projects with output

The first type of question you may be asked is analyzing a project which
produces output.

{% definition(ref="Types of variable costs") %}
- Marginal cost: the cost of producing one more "unit" of output
- Average cost: total cost of producing X "units" divided by the number of units
  produced.
{% end %}

The _break-even point_ corresponds to the production level at which the profit
is zero and the total cost equals the total revenue. The _profit_ is equal to
the _revenue_ after subtracting the total costs.

## Interest rates

When you lend money, you expect to receive the money back with an additional payment called the _interest_.

{% definition(ref="Rate of return (RoR)") %}
The net gain of an investment over a specified time period,
measured as a proportion of the initial investment.
{% end %}

The _interest rate_ is the rate of return you expect when lending the money: the percentage of the original money you lent that you expect as a profit. If you have $P$ dollars and lend them at an interest rate of $i$, the future worth of the money is

$$F = P + Pi = P(1 + i)$$

The interest rate is expressed for a certain time period that may be a year, month, quarter, week, or even a day.
This is called the _interest period_.
The most common period is a year.

{% definition(ref="Nominal interest") %}
_Nominal interest_ is the stated interest on an investment without taking _compounding_ into account.

For example, the nominal annual interest rate is the interest rate per month multiplied by the number of months in a year (12). In general, given the interest rate for a subperiod $i_s$ and the number of subperiods in a period $m$, we have:

$$i_r = i_s \times m$$
{% end %}

{% definition(ref="Compounding interest") %}
_Compounding interest_ allows us to calculate the future value of a loan where money paid in the form of interest after each period is reinvested at the same interest rate.

The future worth $F$ of such a loan with $N$ periods is:

$$F = P(1+i)^{N}$$

The total interest on the loan paid is:

$$I_c = P(1+i)^N - P$$
{% end %}

{% definition(ref="Effective interest") %}
_Effective interest_ $i_e$ is the interest from an investment with interest paid every subperiod for $m$ subperiods, given that the interest is reinvested with compounding. Given the nominal interest per period $i_r$, we have

$$i_e=\left (1+\frac{i_r}{m}\right )^m -1$$
{% end %}

## Project cashflows

Every project can be analyzed in terms of its cashflows.
Given a project with fixed lifespan divided into equal periods of time,
a _cashflow_ is an expected income or expenditure of the project at the end of a certain period.

{% definition(ref="Cash flow diagram") %}
A diagram summarizing all _receipts_ (income) and _disimbursements_ (expenditures) of a project over its lifespan.

- The horizontal axis represents time and is divided into discrete periods (years, months, etc).
- Upward arrows represent positive cashflow and income received at the end of that period.
- Downwards arrows reprsent negative cashflow and expenditures at the end of that period.

We make some assumptions using this tool:

- The end of one period is exactly the beginning of the next.
- All cash flows occur at the end of a time-period.

<center>
<svg version="1.0" viewBox="13 541.45 1340 501.55" xmlns="http://www.w3.org/2000/svg"><mask id="ao" x="637" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="637" y="737" width="26" height="86" fill="#fff"/> <rect x="629" y="767.5" width="42" height="25"/> </mask> <g mask="url(#ao)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m650 750v60" fill="none"/> <path d="m650 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(632 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="m" x="687" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="687" y="737" width="26" height="86" fill="#fff"/> <rect x="679" y="767.5" width="42" height="25"/> </mask> <g mask="url(#m)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m700 750v60" fill="none"/> <path d="m700 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(682 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="a" x="737" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="737" y="737" width="26" height="86" fill="#fff"/> <rect x="729" y="767.5" width="42" height="25"/> </mask> <g mask="url(#a)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m750 750v60" fill="none"/> <path d="m750 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(732 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="aj" x="787" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="787" y="737" width="26" height="86" fill="#fff"/> <rect x="779" y="767.5" width="42" height="25"/> </mask> <g mask="url(#aj)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m800 750v60" fill="none"/> <path d="m800 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(782 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="r" x="837" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="837" y="737" width="26" height="86" fill="#fff"/> <rect x="829" y="767.5" width="42" height="25"/> </mask> <g mask="url(#r)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m850 750v60" fill="none"/> <path d="m850 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(832 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="as" x="887" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="887" y="737" width="26" height="86" fill="#fff"/> <rect x="879" y="767.5" width="42" height="25"/> </mask> <g mask="url(#as)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m900 750v60" fill="none"/> <path d="m900 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(882 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="o" x="937" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="937" y="737" width="26" height="86" fill="#fff"/> <rect x="929" y="767.5" width="42" height="25"/> </mask> <g mask="url(#o)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m950 750v60" fill="none"/> <path d="m950 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(932 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="b" x="987" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="987" y="737" width="26" height="86" fill="#fff"/> <rect x="979" y="767.5" width="42" height="25"/> </mask> <g mask="url(#b)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m1e3 750v60" fill="none"/> <path d="m1e3 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(982 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="ae" x="1037" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="1037" y="737" width="26" height="86" fill="#fff"/> <rect x="1029" y="767.5" width="42" height="25"/> </mask> <g mask="url(#ae)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m1050 750v60" fill="none"/> <path d="m1050 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(1032 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="aq" x="1087" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="1087" y="737" width="26" height="86" fill="#fff"/> <rect x="1079" y="767.5" width="42" height="25"/> </mask> <g mask="url(#aq)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m1100 750v60" fill="none"/> <path d="m1100 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(1082 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="ar" x="1137" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="1137" y="737" width="26" height="86" fill="#fff"/> <rect x="1129" y="767.5" width="42" height="25"/> </mask> <g mask="url(#ar)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m1150 750v60" fill="none"/> <path d="m1150 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(1132 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="ag" x="1187" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="1187" y="737" width="26" height="86" fill="#fff"/> <rect x="1179" y="767.5" width="42" height="25"/> </mask> <g mask="url(#ag)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m1200 750v60" fill="none"/> <path d="m1200 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(1182 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="n" x="1237" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="1237" y="737" width="26" height="86" fill="#fff"/> <rect x="1229" y="767.5" width="42" height="25"/> </mask> <g mask="url(#n)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m1250 750v60" fill="none"/> <path d="m1250 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(1232 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="y" x="1287" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="1287" y="737" width="26" height="86" fill="#fff"/> <rect x="1279" y="767.5" width="42" height="25"/> </mask> <g mask="url(#y)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m1300 750v60" fill="none"/> <path d="m1300 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(1282 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="v" x="387" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="387" y="737" width="26" height="86" fill="#fff"/> <rect x="379" y="767.5" width="42" height="25"/> </mask> <g mask="url(#v)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m400 750v60" fill="none"/> <path d="m400 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(382 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="d" x="437" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="437" y="737" width="26" height="86" fill="#fff"/> <rect x="429" y="767.5" width="42" height="25"/> </mask> <g mask="url(#d)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m450 750v60" fill="none"/> <path d="m450 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(432 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="w" x="487" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="487" y="737" width="26" height="86" fill="#fff"/> <rect x="479" y="767.5" width="42" height="25"/> </mask> <g mask="url(#w)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m500 750v60" fill="none"/> <path d="m500 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(482 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="l" x="587" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="587" y="737" width="26" height="86" fill="#fff"/> <rect x="579" y="767.5" width="42" height="25"/> </mask> <g mask="url(#l)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m600 750v60" fill="none"/> <path d="m600 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(582 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="ad" x="337" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="337" y="737" width="26" height="86" fill="#fff"/> <rect x="329" y="767.5" width="42" height="25"/> </mask> <g mask="url(#ad)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m350 750v60" fill="none"/> <path d="m350 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(332 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="ak" x="287" y="737" width="26" height="126" maskUnits="userSpaceOnUse"> <rect x="287" y="737" width="26" height="126" fill="#fff"/> <rect x="256" y="807.5" width="88" height="25"/> </mask> <g mask="url(#ak)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m300 750v100" fill="none"/> <path d="m300 850 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(259 810.5)" width="82" height="19"> <text x="5.5" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$51m+$15m</text> <text x="76.5" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="ap" x="237" y="737" width="26" height="201" maskUnits="userSpaceOnUse"> <rect x="237" y="737" width="26" height="201" fill="#fff"/> <rect x="225" y="882.5" width="50" height="25"/> </mask> <g mask="url(#ap)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m250 750v175" fill="none"/> <path d="m250 925 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(228 885.5)" width="44" height="19"> <text x="2.5" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$153m</text> <text x="41.5" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="c" x="87" y="737" width="26" height="161" maskUnits="userSpaceOnUse"> <rect x="87" y="737" width="26" height="161" fill="#fff"/> <rect x="75" y="842.5" width="50" height="25"/> </mask> <g mask="url(#c)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m100 750v135" fill="none"/> <path d="m100 885 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(78 845.5)" width="44" height="19"> <text x="2.5" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$136m</text> <text x="41.5" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="x" x="137" y="737" width="26" height="246" maskUnits="userSpaceOnUse"> <rect x="137" y="737" width="26" height="246" fill="#fff"/> <rect x="125" y="927.5" width="50" height="25"/> </mask> <g mask="url(#x)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m150 750v220" fill="none"/> <path d="m150 970 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(128 930.5)" width="44" height="19"> <text x="2.5" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$221m</text> <text x="41.5" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="z" x="187" y="737" width="26" height="316" maskUnits="userSpaceOnUse"> <rect x="187" y="737" width="26" height="316" fill="#fff"/> <rect x="175" y="997.5" width="50" height="25"/> </mask> <g mask="url(#z)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m200 750v290" fill="none"/> <path d="m200 1040 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(178 1000.5)" width="44" height="19"> <text x="2.5" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$289m</text> <text x="41.5" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <g stroke="#fbaf5a" stroke-linecap="round" stroke-linejoin="round" stroke-width="2.25"> <path d="m50 750h1300" fill="none"/> <path d="m1350 750-8.6957-5.75v11.5z" fill="#fbaf5a"/> </g> <g transform="translate(944.5 544.45)"> <rect width="136" height="33" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)"/> </g> <g transform="translate(975.5 551.45) rotate(0 37 9.5)" width="74" height="19" font-size="10pt"> <text x="2.5" y="17" fill="rgb(255, 255, 255)" font-family="Arial">t </text> <text x="10.5" y="17" fill="rgb(255, 255, 255)" font-family="Arial">in </text> <text x="24.5" y="17" fill="rgb(255, 255, 255)" font-family="Arial">months</text> <text x="71.5" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(36 748)"> <rect width="28.899" height="34.75" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(46.449 755.87) rotate(0 4 9.5)" width="8" height="19" font-size="10pt"> <text x="0.5" y="17" fill="rgb(75, 75, 75)" font-family="Lato">0</text> <text x="7.5" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(86 748)"> <rect width="28.918" height="32" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(96.459 754.5) rotate(0 4 9.5)" width="8" height="19" font-size="10pt"> <text x="0.5" y="17" fill="rgb(75, 75, 75)" font-family="Lato">1</text> <text x="7.5" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(136 748)"> <rect width="28.918" height="32" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(146.46 754.5) rotate(0 4 9.5)" width="8" height="19" font-size="10pt"> <text x="0.5" y="17" fill="rgb(75, 75, 75)" font-family="Lato">2</text> <text x="7.5" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(186 748)"> <rect width="28.918" height="32" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(196.46 754.5) rotate(0 4 9.5)" width="8" height="19" font-size="10pt"> <text x="0.5" y="17" fill="rgb(75, 75, 75)" font-family="Lato">3</text> <text x="7.5" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(236 748)"> <rect width="28.918" height="32" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(246.46 754.5) rotate(0 4 9.5)" width="8" height="19" font-size="10pt"> <text x="0.5" y="17" fill="rgb(75, 75, 75)" font-family="Lato">4</text> <text x="7.5" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(286 748)"> <rect width="28.918" height="32" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(296.46 754.5) rotate(0 4 9.5)" width="8" height="19" font-size="10pt"> <text x="0.5" y="17" fill="rgb(75, 75, 75)" font-family="Lato">5</text> <text x="7.5" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(335 750)"> <rect width="28.899" height="34.75" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(345.45 757.87) rotate(0 4 9.5)" width="8" height="19" font-size="10pt"> <text x="0.5" y="17" fill="rgb(75, 75, 75)" font-family="Lato">6</text> <text x="7.5" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(386 748)"> <rect width="28.918" height="32" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(396.46 754.5) rotate(0 4 9.5)" width="8" height="19" font-size="10pt"> <text x="0.5" y="17" fill="rgb(75, 75, 75)" font-family="Lato">7</text> <text x="7.5" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(436 748)"> <rect width="28.918" height="32" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(446.46 754.5) rotate(0 4 9.5)" width="8" height="19" font-size="10pt"> <text x="0.5" y="17" fill="rgb(75, 75, 75)" font-family="Lato">8</text> <text x="7.5" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(486 748)"> <rect width="28.918" height="32" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(496.46 754.5) rotate(0 4 9.5)" width="8" height="19" font-size="10pt"> <text x="0.5" y="17" fill="rgb(75, 75, 75)" font-family="Lato">9</text> <text x="7.5" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(535 740)"> <rect width="34.999" height="49.729" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(544.5 755.36) rotate(0 8 9.5)" width="16" height="19" font-size="10pt"> <text x="1" y="17" fill="rgb(75, 75, 75)" font-family="Lato">10</text> <text x="15" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(585 749.75)"> <rect width="34.998" height="30.73" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(594.5 755.61) rotate(0 8 9.5)" width="16" height="19" font-size="10pt"> <text x="1" y="17" fill="rgb(75, 75, 75)" font-family="Lato">11</text> <text x="15" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(635 749.75)"> <rect width="34.998" height="30.73" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(644.5 755.61) rotate(0 8 9.5)" width="16" height="19" font-size="10pt"> <text x="1" y="17" fill="rgb(75, 75, 75)" font-family="Lato">12</text> <text x="15" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(685 749.75)"> <rect width="34.998" height="30.73" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(694.5 755.61) rotate(0 8 9.5)" width="16" height="19" font-size="10pt"> <text x="1" y="17" fill="rgb(75, 75, 75)" font-family="Lato">13</text> <text x="15" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(735 749.75)"> <rect width="34.998" height="30.73" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(744.5 755.61) rotate(0 8 9.5)" width="16" height="19" font-size="10pt"> <text x="1" y="17" fill="rgb(75, 75, 75)" font-family="Lato">14</text> <text x="15" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(785 749.75)"> <rect width="34.998" height="30.73" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(794.5 755.61) rotate(0 8 9.5)" width="16" height="19" font-size="10pt"> <text x="1" y="17" fill="rgb(75, 75, 75)" font-family="Lato">15</text> <text x="15" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(835 749.75)"> <rect width="34.998" height="30.73" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(844.5 755.61) rotate(0 8 9.5)" width="16" height="19" font-size="10pt"> <text x="1" y="17" fill="rgb(75, 75, 75)" font-family="Lato">16</text> <text x="15" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(885 749.75)"> <rect width="34.998" height="30.73" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(894.5 755.61) rotate(0 8 9.5)" width="16" height="19" font-size="10pt"> <text x="1" y="17" fill="rgb(75, 75, 75)" font-family="Lato">17</text> <text x="15" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(935 749.75)"> <rect width="34.998" height="30.73" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(944.5 755.61) rotate(0 8 9.5)" width="16" height="19" font-size="10pt"> <text x="1" y="17" fill="rgb(75, 75, 75)" font-family="Lato">18</text> <text x="15" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(985 750)"> <rect width="34.998" height="30.73" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(994.5 755.86) rotate(0 8 9.5)" width="16" height="19" font-size="10pt"> <text x="1" y="17" fill="rgb(75, 75, 75)" font-family="Lato">19</text> <text x="15" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(1035 749.75)"> <rect width="34.998" height="30.73" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(1044.5 755.61) rotate(0 8 9.5)" width="16" height="19" font-size="10pt"> <text x="1" y="17" fill="rgb(75, 75, 75)" font-family="Lato">20</text> <text x="15" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(1085 749.75)"> <rect width="34.998" height="30.73" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(1094.5 755.61) rotate(0 8 9.5)" width="16" height="19" font-size="10pt"> <text x="1" y="17" fill="rgb(75, 75, 75)" font-family="Lato">21</text> <text x="15" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(1135 750)"> <rect width="34.998" height="30.73" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(1144.5 755.86) rotate(0 8 9.5)" width="16" height="19" font-size="10pt"> <text x="1" y="17" fill="rgb(75, 75, 75)" font-family="Lato">22</text> <text x="15" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(1185 749.75)"> <rect width="34.998" height="30.73" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(1194.5 755.61) rotate(0 8 9.5)" width="16" height="19" font-size="10pt"> <text x="1" y="17" fill="rgb(75, 75, 75)" font-family="Lato">23</text> <text x="15" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(1235 750)"> <rect width="34.998" height="30.73" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(1244.5 755.86) rotate(0 8 9.5)" width="16" height="19" font-size="10pt"> <text x="1" y="17" fill="rgb(75, 75, 75)" font-family="Lato">24</text> <text x="15" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <g transform="translate(1285 749.75)"> <rect width="34.998" height="30.73" fill="rgba(255,255,255,0.01)" stroke="rgba(255,255,255,0.01)" stroke-linecap="round" stroke-linejoin="round" stroke-width="NaN"/> </g> <g transform="translate(1294.5 755.61) rotate(0 8 9.5)" width="16" height="19" font-size="10pt"> <text x="1" y="17" fill="rgb(75, 75, 75)" font-family="Lato">25</text> <text x="15" y="17" fill="#4b4b4b" font-family="noto_regular"/> </g> <mask id="an" x="287" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="287" y="677" width="26" height="85" fill="#fff"/> <rect x="273" y="707" width="54" height="25"/> </mask> <g mask="url(#an)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m300 749v-59" fill="none"/> <path d="m300 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(276 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="s" x="337" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="337" y="677" width="26" height="85" fill="#fff"/> <rect x="323" y="707" width="54" height="25"/> </mask> <g mask="url(#s)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m350 749v-59" fill="none"/> <path d="m350 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(326 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="j" x="387" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="387" y="677" width="26" height="85" fill="#fff"/> <rect x="373" y="707" width="54" height="25"/> </mask> <g mask="url(#j)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m400 749v-59" fill="none"/> <path d="m400 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(376 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="p" x="437" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="437" y="677" width="26" height="85" fill="#fff"/> <rect x="423" y="707" width="54" height="25"/> </mask> <g mask="url(#p)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m450 749v-59" fill="none"/> <path d="m450 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(426 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="q" x="487" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="487" y="677" width="26" height="85" fill="#fff"/> <rect x="473" y="707" width="54" height="25"/> </mask> <g mask="url(#q)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m500 749v-59" fill="none"/> <path d="m500 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(476 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="ah" x="587" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="587" y="677" width="26" height="85" fill="#fff"/> <rect x="573" y="707" width="54" height="25"/> </mask> <g mask="url(#ah)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m600 749v-59" fill="none"/> <path d="m600 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(576 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="af" x="637" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="637" y="677" width="26" height="85" fill="#fff"/> <rect x="623" y="707" width="54" height="25"/> </mask> <g mask="url(#af)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m650 749v-59" fill="none"/> <path d="m650 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(626 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="h" x="687" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="687" y="677" width="26" height="85" fill="#fff"/> <rect x="673" y="707" width="54" height="25"/> </mask> <g mask="url(#h)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m700 749v-59" fill="none"/> <path d="m700 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(676 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="i" x="737" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="737" y="677" width="26" height="85" fill="#fff"/> <rect x="723" y="707" width="54" height="25"/> </mask> <g mask="url(#i)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m750 749v-59" fill="none"/> <path d="m750 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(726 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="ac" x="887" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="887" y="677" width="26" height="85" fill="#fff"/> <rect x="873" y="707" width="54" height="25"/> </mask> <g mask="url(#ac)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m900 749v-59" fill="none"/> <path d="m900 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(876 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="f" x="837" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="837" y="677" width="26" height="85" fill="#fff"/> <rect x="823" y="707" width="54" height="25"/> </mask> <g mask="url(#f)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m850 749v-59" fill="none"/> <path d="m850 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(826 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="t" x="787" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="787" y="677" width="26" height="85" fill="#fff"/> <rect x="773" y="707" width="54" height="25"/> </mask> <g mask="url(#t)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m800 749v-59" fill="none"/> <path d="m800 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(776 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="aa" x="937" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="937" y="677" width="26" height="85" fill="#fff"/> <rect x="923" y="707" width="54" height="25"/> </mask> <g mask="url(#aa)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m950 749v-59" fill="none"/> <path d="m950 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(926 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="au" x="987" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="987" y="677" width="26" height="85" fill="#fff"/> <rect x="973" y="707" width="54" height="25"/> </mask> <g mask="url(#au)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m1e3 749v-59" fill="none"/> <path d="m1e3 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(976 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="ab" x="1037" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="1037" y="677" width="26" height="85" fill="#fff"/> <rect x="1023" y="707" width="54" height="25"/> </mask> <g mask="url(#ab)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m1050 749v-59" fill="none"/> <path d="m1050 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(1026 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="ai" x="1187" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="1187" y="677" width="26" height="85" fill="#fff"/> <rect x="1173" y="707" width="54" height="25"/> </mask> <g mask="url(#ai)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m1200 749v-59" fill="none"/> <path d="m1200 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(1176 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="al" x="1237" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="1237" y="677" width="26" height="85" fill="#fff"/> <rect x="1223" y="707" width="54" height="25"/> </mask> <g mask="url(#al)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m1250 749v-59" fill="none"/> <path d="m1250 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(1226 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="u" x="1287" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="1287" y="677" width="26" height="85" fill="#fff"/> <rect x="1273" y="699" width="54" height="41"/> </mask> <g mask="url(#u)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m1300 749v-59" fill="none"/> <path d="m1300 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(1276 702)" width="48" height="35"> <text x="3" y="14" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="14" fill="rgb(75, 75, 75)" font-family="Lato" font-size="10pt"/> <text x="24" y="36" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="am" x="1087" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="1087" y="677" width="26" height="85" fill="#fff"/> <rect x="1073" y="707" width="54" height="25"/> </mask> <g mask="url(#am)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m1100 749v-59" fill="none"/> <path d="m1100 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(1076 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="at" x="1137" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="1137" y="677" width="26" height="85" fill="#fff"/> <rect x="1123" y="707" width="54" height="25"/> </mask> <g mask="url(#at)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m1150 749v-59" fill="none"/> <path d="m1150 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(1126 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="e" x="537" y="737" width="26" height="86" maskUnits="userSpaceOnUse"> <rect x="537" y="737" width="26" height="86" fill="#fff"/> <rect x="529" y="767.5" width="42" height="25"/> </mask> <g mask="url(#e)" stroke="#9c9" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m550 750v60" fill="none"/> <path d="m550 810 6.4972-6.9565m-6.4972 6.9565-6.4972-6.9565z" fill="#fff"/> </g> <g transform="translate(532 770.5)" width="36" height="19"> <text x="2" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$15m</text> <text x="34" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="g" x="537" y="677" width="26" height="85" maskUnits="userSpaceOnUse"> <rect x="537" y="677" width="26" height="85" fill="#fff"/> <rect x="523" y="707" width="54" height="25"/> </mask> <g mask="url(#g)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m550 749v-59" fill="none"/> <path d="m550 690-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(526 710)" width="48" height="19"> <text x="3" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$4.75m</text> <text x="45" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> <mask id="k" x="37" y="567" width="26" height="195" maskUnits="userSpaceOnUse"> <rect x="37" y="567" width="26" height="195" fill="#fff"/> <rect x="15" y="597.5" width="70" height="25"/> </mask> <g mask="url(#k)" stroke="#c9f" stroke-linecap="round" stroke-linejoin="round" stroke-width="1.5"> <path d="m50 749v-169" fill="none"/> <path d="m50 580-6.4972 6.9565m6.4972-6.9565 6.4972 6.9565z" fill="#fff"/> </g> <g transform="translate(18 600.5)" width="64" height="19"> <text x="4" y="17" fill="rgb(75, 75, 75)" font-family="Lato" font-size="9pt">$213.77m</text> <text x="60" y="17" fill="#4b4b4b" font-family="noto_regular" font-size="10pt"/> </g> </svg> 
</center>
{% end %}

## Time value of money

An essential part of calculating the worth of projects is the _time value of money_.
This is the concept that money now is always worth more than money in the future, because money now can work for you now.

We quantify the greater benefit of "money now" using a _discounting rate_, which is an interest rate used to compare cash flows at different points in time.

Given an discounting rate $i$ compounding after each equal period of time $t$, the future worth of assets after $Nt$ equal periods if they are worth $P$ at present value is:

$$F=P(1+i)^N$$

while the present worth of assets worth $F$, $Nt$ in the future, is:

$$P=F(1+i)^{-N}$$

The discounting rate we use depends, but in general, it is the interest that our assets would be expected to earn if they were invested passively (the money earned from "doing nothing").
A commonly-used discounting rate is the minimum acceptable rate of return (MARR) of a business since we assume the business will be able to achieve this return without investing in any projects, but selection of the discounting rate will depend on the situation.

In general, projects that deliver less net benefit than simply lending out the capital will not be selected.

## Comparing project cash flows

We want to calculate a single value to compare the "worthiness" of multiple projects.
Because money has different value in time (present always greater than future), cash flows cannot be compared directly.
Instead, we generate a _net present value_ (NPV), _net future value_ (NFV), or _annualized value_ for each project.

We use our understanding of the time value of money and three fundamental series: the _annuity_, _arithmetic gradient_, and _geometric gradient series_ to do this using our [factors](./#appendix).
Our fundamental assumption is that every cash flow occurs at the very end of a period.

{% definition(ref="Annuity") %}
An _annuity_ is a uniform series of cash flows that start at the end of the first period and continue for $N$ periods.
Given an annuity of payment $A$ over $N$ equal periods with interest rate $i$, the future worth is equal to:

$$F = A\frac{(1+i)^N - 1}{i}$$

They are used to model operation and maintenance costs (O&M), mortgage payments, lease payments, and utility payments.
{% end %}

{% definition(ref="Arithmetic gradient series") %}
Series of cash flows that start at zero and increase/decrease by a constant amount, $G$, from period to period with final payment on last period $N$.
The future value of this series is

$$F = \frac{G}{i}\left [\frac{(1+i)^N - 1}{i} - N \right ]$$
{% end %}

A common pattern is combining a fixed annuity with an arithmetic gradient series to represent fixed and constant cash flows.
Deal with non-standard annuities by treating each cash flow in the annuity or gradient individually and changing the compounding period.

{% definition(ref="Geometric gradient series") %}
Cash flows that increase or decrease by a constant percentage each period.

Given base value of the series $A$ and rate of growth $g$, we have the following _present value_:

$$P = A\left [ \frac{1-\left (\frac{1+g}{1+i}\right )^n}{i - g} \right ], g\ne i$$

We call $i_o = \frac{1+g}{1+i} - 1$ the _growth adjusted interest rate_.
{% end %}

Steps to compare projects using net present/future/annual worth:

1. Identify single capital costs, fixed repeating costs, and variable repeating costs.
	- Single capital costs should be "brought to the present/future" directly.
	- _Fixed repeating costs_ should be modelled with an annuity.
	- _Variable repeating costs_ should be modelled with an arithmetic/geometric series.
2. For each pattern, calculate present/future worth using a factor.
3. Cost is additive: add all the present/future costs calculated to get the _estimated present/future cost_.
4. Identify windfall income, fixed incomes, and variable incomes.
5. Calculate present/future worth for each similarly.
6. Add all present/future income calculated to get the _estimated present/future income_.
7. Subtract present/future cost from present/future income to get _net present/future value_.
8. If the question wants an annualized worth, convert this one value into an annuity using the _capital recovery factor_. 

## Depreciation

The decrease in utility of fixed assets with time.
Firms calculate asset depreciation.

The costs of fixed assets are not treated simply as expenses to be accounted for in the year that they are acquired.
They are _capitalized_: their costs are distributed by subtracting them as expenses from gross income.

The systematic allocation of the initial cost of an asset in parts over time (the asset's _depreciable life_ is called accounting deprecation.

- _Cost basis_: total costs claimed as an expense over an asset's life. Sum of annual depreciation expenses
- _Useful life_: estimation of duration over which asset expected to fulfill intended purpose.
- _Salvage value_: asset's value at end of life.

Straight-line method: assumes rate of loss in value is ocnstant over useful life: $D = \frac{P-S}{N}$, where $P$ is purchase price, $S$ is salvage value, and $N$ is periods of use.

Declining-balance method assumes that loss in value is constant fraction of asset's book value at end of last period.

$D_n = dP(1-d)^{n-1}$

$D_n$ is deprecation charge for period $n$, $d$ is depreciation rate, $P$ is purchase price of asset, $n$ is the period.

## Comparison methods

We only take investment opportunities with returns outweighing the costs.

Our comparsion methods make several assumptions:

- measure all costs and benefits in terms of money
- future cash flows may be determined
- no inflation or deflation in cash flows
- sufficient funds to implement all projects in consideration
- do not consider taxes
- all investments have initial costs and investment
- cash generated by the project is reinvested into the project at a rate equal to the discount rate (MARR) which does not change during project duration.

Projects may be independent (do not relate to one another), mutually exclusive (cannot be implemented at the same time), or related but not mutually exclusive (depend on each other).

To consider whether or not to implement multiple projects, divide them into all possible sets of projects that may be done concurrently and evaluate each.

Projects may be _contingent_ or depend on each other. That is, B iff A.

{% definition(ref="Minimum Accpetable Rate of Return (MARR) %}
The minimum return (expressed as an interest rate) that investors expect on any investment.

All projects must meet this return to be _feasible_.
{% end %}

For multiple independent projects, we evaluate each and see if the net present worth is greater than the zero using the MARR as the interest rate.

For mutually exclusive projects with same service life, we prefer the project with the greatest net present worth.

Annual worth analysis: we convert all cash flows into a single annuity. Annual equivalent cost (AEC).

Called "capital cost" when referring to annual equivalent of initial investment + salvage value.

Future worth: we calculate future values, same as NPW analysis.

## Payback period analysis

Rough estimation of the time it takes for an investment to pay for itself.

$$\text{Payback period} = \frac{Initial investment}{Annual savings}$$

The project with the shortest payback period is the preferred investment.

If annual savings are not constant, calculate by deducting each year of savings from the first cost until the first cost is recovered and count the number of deductions.

Advantages: accounts for need of quick capital recovery
Disadvantages: ignores time value of money and expected service life and discriminates against long-term projects.

{% definition(ref="Discounted payback period") %}
A payback period calculation that accounts for the interest rate:

$$\text{Discounted PP} = \frac{\text{Initial cost}}{\sum^U_{k=0}(1+i)^{-k}\cdot A_k}$$

where $U$ is period at which the cumulative discounted annual savings equals the first cost.
{% end %}

## Internal rate of return

{% definition(ref="Rate of return (RoR)") %}
The net gain of an investment over a specified time period,
measured as a proportion of the initial investment.
{% end %}

{% definition(ref="Internal rate of return (IRR)") %}
The interest rate, $i^\*$, that allows a project to break even, assuming that cash flows generated by the project are reinvested at this interest rate.

It is calculated as the $i^\*$ that makes cash inflows equal to the cash outflows.

$$\sum^N_{k=0} \frac{R_k}{(1+i^\*)^k} = \sum^N_{k=0}\frac{D_k}{(1+i^\*)^k}$$
{% end %}

We calculate the IRR by using the bisection method on a function of net present worth and guessing until we find the root of this function.

The IRR should be compared with the minimum acceptable rate of return. Projects with $\text{IRR}\ge\text{MARR}$ are attractive because the money invested is earning as much or greater than if it were invested elsewhere.

Note: for mutually exclusive projects: the project with highest IRR may not be preferred alternative. HTe NPW, AW, and NFW are absolute measures of investment worth while the IRR is a relative measure, such that lower IRR projects may generate more
profits than a higher one. therefore IRR and NPW may yield different conclusions. 
Make sure altneratives have equal lives.

- Individual projects: accept all projects for which $i^\* > \text{MARR}$; otherwise reject
- Mutually-exclusive projects:
	1. rank projects from $1$ to $n$ in increasing order of initial cost
	2. Compare projects $1$ and $2$. If the incremental IRR of 2 relative to one is less than the MARR, discard current challenger.
	3. If the increment IRR is greater, discard $1$ and replace it with $2$.
	4. Continue until there are no more projects to compare

Mutiple IRRs may be calculated depending on the Nth degree polynomial we solve.

Simple investments: initial cash flow negative, only one sign change. always have unique IRR.

Non-simple investment: Cash flows may have more than one sign change. May have multiple IRRs

Neither: positivie initial investment.

Selection for simple investments: MARR < $i$ should be accepted.

Non-simple investments: accept if all IRRs > MARR, else decline.

Borrowing cash flow: has single IRR.

To see if project has multiple IRRs: use decartes rule (number of positive real values of IRR is never greater than number of sign changes in cash flow sequence)

And Norstrom's criterion: if series $S_k$ is cash flow accumulated till year $k$, starts negatively and changes sign only once, a unique IRR exists.


## External rate of return

When multiple IRR are obtained, consider returns earned by money associated with a project but not invested in the project. THe external rate of return, $i^\*\_e$ is the rate of return where any cash flows not invested in the rpoject are assumed to
earn interest at a predeterminedd rate (MARR). A project may only ever have one ERR given a MARR.

To determine if there is "cash in hand", we must use the project's balance which depends on the ERR used to discount the cashflows.

Series people: each project balance is the partial sum of the total cash flow for each period $0, 1, \ldots, N$.

$B_0 = F_0$

$B_1 = F_0(1+i)^1 + F_1$

$B_2 = F_0(1+i)^2 + F_1(1+i)^1 + F_2$

where $F_0$ is sum of cashflows for period $0$.

Each positive $B_k$ is a source of funds up to the next $k+1$ period.

Then the ERR is equal to the root such that the $B_N$ balance is 0.

Approximate ERR: calcuate future value at year $N$ of all net receipts at MARR
2. calculate future value at year $N$ of all net disbursements at aERR $i^\*\_\text{ea}$.
Equate both and solve for aERR.

Modified internal rate of return: uses the rate at which firms invest $i_\text{inv}$ and the rate at which firms borrow for IRR equation. Claculate present worth of all costs using rate for borrowing $i_\text{fin}$ and future worth of all receipts using rate of investment.
using rate for investments and find MIRR making present and future worths equivalent.

## Public and private projects

In private sector, we launch a project by using a pre-determined discount rate (MARR).

In public sector, we sometimes launch projects with no monetary profits.

Hard to select interest rates: MARR is usually low to make investments look attractive. We can use Weighted Average Cost of Capital to consider multiple sources of funding.

Costs: sponsor's costs with initial costs well known and future O&M estimated

Benefits: very hard to estimate. We may state advantages to the public in quantified dollar values.
Disbenefits: may also be given a cost, but are very ahrd to estimate and convert into dollar amounts.

{% definition(ref="Benefit-cost ratio (BCR)") %}

$$\text{BCR} = \frac{\text{PW}(\text{Benefits})}{\text{PW}(\text{Costs})}$$

We may also use the future-worth and annual-worth functions instead of present-worth.

This formula may be made as complicated as possible: modified

$$\text{BCRM} = \frac{\text{PW}(\text{Benefits - Social costs - O\\&M})}{\text{PW}(\text{Capital costs})}$$
{% end %}

Steps:

1. Assign a life of $N$ years
2. Estimate sponsor's costs, social benefits, social costs.
3. Assign an interest rate to the project, $i$ (annual %)
4. Convert all amounts to present/future/annual worth
5. Calculate BCR using conventional or modified equation.
6. If $BCR>1$, accept; $BCR<1$, reject. $BRC\approx 1$, indeterminate. Do nothing is an acceptable course of action.

Incremental BCR: order alternatives $X$ and $Y$ using ascending order of PW of total cost. Then 

$$\Delta BCR = BCR(X-Y)$$

BCR is primarily public sector.

## Risk and uncertainity

We may sometimes have to account for for changing project parameters (cash flows change in timing and size).

A _sensitivity graph_ are used to assess the effect of a one-time change in key project parameters.

1. Define a base case and calculate PW or IRR, and other metrics.
2. Vary a parameter at a time and determine impact on NPW, IRR, or other metrics.

We may draw a graph by adding the variance using a variable $p$ and thus creating a formula.

Shortcomings: impact of parameter variations outside range considered may not be linear extrapolation of graph lines.

Interaction between the parameters are not considered.

Attitude towards risk is a general way of classifying risk preferences:

- risk averse: fear of loss
- risk neutral: indifferent
- risk taker: lesser fear of loss

We may measure risk in terms of standard deviation: dispersion of outcomes about expected value.

Break-even analysis: varying a problem parameter and determining what parameter value causes the performance to reach a threshold.

We use NPW and a break-even of zero to evaluate projects, given any uncertain parameter like MARR.

Risk adjusted MARR: use higher discount rates for alternatives with a higher degree of uncertainity.
A higher MARR implies distant cash flows are less important than current, near term cash flows.

Uncertainity howerver is not made explicit.

Given projects with same NPV and compared with same MARR, choose less risky investment.

Expected value:

$\overline{x}=E(x)=\sum^m_{i=1}x_i p(x_i)$

Standard deviation:

$$\sigma = \sqrt{E(X^2) - [E(X)]^2}$$




## Appendix

_Factor table_:

|Name|Factor|Equation|
|---|---|---|
|Compound amount factor|(F/P, i, N)|$(1+i)^N$|
|Present worth factor|(P/F, i, N)|$(1+i)^{-N}$|
|Uniform series CAF|(F/A, i, N)|$i^{-1}[(1+i)^N - 1]$|
|Sinking fund factor|(A/F, i, N)|$i[(1+i)^N - 1]^{-1}$|
|Capital recovery factor|(A/P, i, N)|$i(1+i)^N[(1+i)^N - 1]^{-1}$|
|Series present worth factor|(P/A, i, N)|$[(1+i)^N-1]i^{-1}(1+i)^{-N}$|
|Arithmetic gradient PWF|(P/G, i, N)|$[(1+i)^N - iN - 1]i^{-2}(1+i)^{-N}$|
|Arithmetic gradient USF|(A/G, i, N)|$i^{-1} - N[(1+i)^N - 1]^{-1}$|
