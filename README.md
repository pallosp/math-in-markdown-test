# Math in Markdown rendering tests

Tests math expression support in the VSCode, GitHub and npmjs.com Markdown renderers.

## Simple Unicode

- Normal (`√(x²+1)`) ⟶ √(x²+1)
- Italic (`_√(x²+1)_`) ⟶ _√(x²+1)_
- Bold (`**√(x²+1)**`) ⟶ **√(x²+1)**
- Code (`` `√(x²+1)` ``) ⟶ `√(x²+1)`
  
**Conclusion**: works everywhere.

## HTML superscript

- `√(x<sup>2</sup>+1)` ⟶ √(x<sup>2</sup>+1)

**Conclusion**: works everywhere.

## R Markdown superscript

https://rmarkdown.rstudio.com/authoring_basics.html

- `√(x^2^+1)` ⟶ √(x^2^+1)

**Conclusion**: proprietary syntax, none of VSCode, GitHub or npmjs understand it.

## Inline equation (`$...$`)

- `$√(x²+1)$` ⟶ $√(x²+1)$
- `$√(x^2+1)$` ⟶ $√(x^2+1)$
- `$\sqrt{x²+1}$` ⟶ $\sqrt{x²+1}$
- `$\sqrt{x^2+1}$` ⟶ $\sqrt{x^2+1}$
- `$\frac{1}{2}$` ⟶ $\frac{1}{2}$

**Conclusion**: works in VSCode and on GitHub modulo minor vertical alignment
issues in the latter.

## Inline equation, GitHub style (````$`...`$````)

https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions

````$`\sqrt{x²+1}`$```` ⟶ $`\sqrt{x²+1}`$  

**Conclusion**: Only works on GitHub. VSCode renders the backticks
verbatim. npmjs.com doesn't support such expressions at all.

## Display equation (`$$...$$`)

`$$\frac{x+1}{2}$$`

$$\frac{x+1}{2}$$

`$$ \frac{x+1}{2} $$`

$$ \frac{x+1}{2} $$

`$$\frac{x+1}{2}$$` (no blank line before expression)
$$\frac{x+1}{2}$$

**Conclusion**: Works in VSCode. GitHub requires a blank line before the
equation. npmjs.com doesn't support such equations at all.

## Math block (<code>```math</code>)

````
```math
\sqrt{x^2+1}
```
````

```math
\sqrt{x^2+1}
```

**Aligned equations**

````
```math
\begin{aligned}
  x+1 &= y \\
  x &= y-1
\end{aligned}
```
````

```math
\begin{aligned}
  x+1 &= y \\
  x &= y-1
\end{aligned}
```

**Conclusion**: simple expressions work both in VSCode and on GitHub. The latter
struggles with the equation alignment.

## MathML

```html
<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<mrow>
  <mi>x</mi>
  <mo>=</mo>
  <mfrac>
    <mrow>
      <mrow>
        <mo>-</mo>
        <mi>b</mi>
      </mrow>
      <mo>±</mo>
      <msqrt>
        <mrow>
          <msup>
            <mi>b</mi>
            <mn>2</mn>
          </msup>
          <mo>-</mo>
          <mrow>
            <mn>4</mn>
            <mo>⁢</mo>
            <mi>a</mi>
            <mo>⁢</mo>
            <mi>c</mi>
          </mrow>
        </mrow>
      </msqrt>
    </mrow>
    <mrow>
      <mn>2</mn>
      <mo>⁢</mo>
      <mi>a</mi>
    </mrow>
  </mfrac>
</mrow>
</math>
```

<math xmlns="http://www.w3.org/1998/Math/MathML" display="block">
<mrow>
  <mi>x</mi>
  <mo>=</mo>
  <mfrac>
    <mrow>
      <mrow>
        <mo>-</mo>
        <mi>b</mi>
      </mrow>
      <mo>±</mo>
      <msqrt>
        <mrow>
          <msup>
            <mi>b</mi>
            <mn>2</mn>
          </msup>
          <mo>-</mo>
          <mrow>
            <mn>4</mn>
            <mo>⁢</mo>
            <mi>a</mi>
            <mo>⁢</mo>
            <mi>c</mi>
          </mrow>
        </mrow>
      </msqrt>
    </mrow>
    <mrow>
      <mn>2</mn>
      <mo>⁢</mo>
      <mi>a</mi>
    </mrow>
  </mfrac>
</mrow>
</math>

**Conclusion**: only works in VSCode.

## CodeCogs

The expressions below are SVGs created with the
[CodeCogs equation editor](https://editor.codecogs.com/) and embedded from
latex.codecogs.com.

- Inline formula: ![inline formula](https://latex.codecogs.com/svg.image?\sqrt{x^2&plus;1})
- Inline fraction, 5 pt: ![inline fraction](https://latex.codecogs.com/svg.image?\tiny&space;\frac{1}{2})
- Vertical centering with `<span style="vertical-align: middle">`: <span style="vertical-align: middle">![inline fraction](https://latex.codecogs.com/svg.image?\tiny&space;\frac{1}{2})</span>  

**Conclusion**: works, but vertical alignment is off in most cases.
GitHub and npmjs don't support fine tuning it with CSS.
