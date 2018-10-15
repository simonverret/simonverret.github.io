---
layout: post
title:  "Bare dispersion of cuprates"
categories:
comments: true
mathjax: true
---

It is often useful to explore the simplest model describing high temperature superconducting cuprates. In 2D, this model is simply given by the following energy function:

$$ \xi_{\vec k} = -2t(\cos k_x + \cos k_y) - 2t'(\cos (kx+k_y) + \cos (kx+k_y)) - \mu$$

Of course, such a simple model does not contain superconductivity. As a function of $k_x$ and $k_y$, this energy function yields:

<img src="/img/CupratesMovie.gif" title="Cuprates in GIF" />

where the chemical potential $\mu$ changes with time. The Mathemtatica code to produce the above animation is given below. On the right, I plot the energy contour $ \xi_{\vec k} = 0$ as a function of $k_x$ and $k_y$, and the spectral weight at the Fermi level $A(\vec k, \epsilon=0)$, which are the same in this case. The spectral weight is given by:

$$ A(\vec k, \epsilon) = -\frac{1}{\pi}\text{Im}\left\{\frac{1}{\epsilon+i0^{+}-\xi(\vec k)}\right\}$$

where $0^+$ takes the arbitrary value of 0.05.


{% highlight mathematica %}
{% raw  %}

xi[kx_, ky_] = -2*(Cos[kx] + Cos[ky]) + 
   2*0.35*(Cos[kx + ky] + Cos[kx - ky]);
spectralWeight[kx_, ky_, w_, mu_] := 
  0.05/((w - xi[kx, ky] + mu)^2 + 0.05^2)/Pi;

spWeightColor[x_] := 
  Blend[{{0, LightGray}, {1, RGBColor[1, 0, 0, 1]}}, x];
SetOptions[Plot3D, Mesh -> None, Boxed -> False, Ticks -> None, 
  Axes -> False, PlotRange -> Full, BoxRatios -> {1, 1, 0.6}, 
  BoundaryStyle -> None, MaxRecursion -> 7, ClippingStyle -> None, 
  Ticks -> None, 
  Lighting -> {{"Point", White, {0, 0, 12}}, {"Point", 
     White, {-20, -20, 0}}}, ViewPoint -> {-10, -5, 4}];
SetOptions[ContourPlot, FrameTicks -> None, Frame -> None, 
  AspectRatio -> 1];
SetOptions[DensityPlot, FrameTicks -> None, PlotPoints -> 70, 
  Frame -> None, AspectRatio -> 1, ColorFunction -> spWeightColor];

x = 0.16;
T = Table[
   GraphicsRow[{
     Plot3D[{xi[kx, ky], mu - 0.03}, {kx, -Pi, Pi}, {ky, -Pi, Pi}, 
      PlotRange -> {-4, 6}, 
      PlotStyle -> {{RGBColor[0.45, 0.35, 0.7, 1], 
         Opacity[1]}, {White, Opacity[0.7]}, {White, Opacity[0.8]}}, 
      MeshStyle -> Directive[Thickness -> 0.01, Red], 
      MeshFunctions -> {#3 &}, Mesh -> {{mu}}
      ],
     GraphicsRow[{
       ContourPlot[{xi[kx, ky] == mu}, {kx, -Pi, Pi}, {ky, -Pi, Pi}, 
        ContourStyle -> {Thickness -> 0.01, Red}, 
        Prolog -> {LightGray, 
          Rectangle[Scaled[{0, 0}], Scaled[{1, 1}]]}
        ],
       DensityPlot[
        spectralWeight[kx, ky, 0, mu], {kx, -Pi, Pi}, {ky, -Pi, Pi}, 
        PlotRange -> {0, 10}]
       }]
     }, ImageSize -> Full, Background -> White]
   , {mu, Range[-300, 350, 50]/100.0 + 0.01}];

Export["CupratesMovie.gif", Join[T, Reverse[T]], 
 "AnimationRepetitions" -> Infinity]

{% endraw %}
{% endhighlight %}

