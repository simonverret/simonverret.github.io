---
layout: post
title:  "Carrier density in a 2D antiferromagnet"
categories:
comments: true
mathjax: true
---

In <a href="https://www.nature.com/articles/nature16983">this 2016 Nature paper</a> by Badoux _et al._, the Hall number goes from $p$ to $1+p$ as a function of doping. What is the intuition behind this result? Not all people find this question easy, and some might think it is easier than it actually is. To see what I mean, consider the following antiferromagnetic (AF) reconstruction of the [typical Fermi surface for cuprates]({% post_url 2018-10-05-dispersion-of-cuprates %}):

<img class="center" src="/img/dividingBrillouin-01.png"  title="dividing the Brillouin zone" width="1000px"/>

First, remember that the Brillouin zone contains 2 states per unit-cell of the lattice (one for each spin). On the left, we count one carrier in each _reduced_ Brillouin zones of the AF reconstruction. In the middle, when the hole doping is $p$, we see that the Fermi surface splits the total volume in $n=1-p$ electrons below the Fermi level, and $1+p$ holes above the Fermi level. As you can see above, it is the difference between the red portion and blue portion that give $p$. 

<img class="center" src="/img/dividingBrillouin-02.png"  title="Increasing the gap at fixed chemical potential" width="1000px"/>

When the gap opens, the red and blue volumes get smaller. If the doping before we open the gap is non-zero, $p\neq0$, and we fix the chemical potential while we open the gap, this change in size must result in a change of doping. This is important. It means that once the gap is open, the chemical potential must change to conserve particle number. Thus, the carrier number is not $p$ because the pocket has a volume of $p$, it is $p$ because particle number is conserved.

This is why I say the $p$ to $1+p$ result is not as easy as it seems. The reason the Hall number goes from $p$ to $1+p$, in the AF scenario, is that the upper band, the one associated with the blue electon pockets, completely leave the Fermi surface. The system loses one carrier per unit-cell. The leftover lower band, associated with the red hole pockets, contains $p$ carrier, not because the leftover volume is $p$, but because it has to, in order to conserve particle number.

In cuprates, antiferromagnetism does not extend that far in doping, and thus this picture should not hold. However, if Mott physics is involved, there is a good change that the split in two bands remains a good approximation. What remains unclear, in that case, is if the upper band will remain a sharp band, or become incoherent spectral weight, and also if the bottom band will actually form a close pocket. To my knowledge, these are open questions.