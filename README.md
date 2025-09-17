# Math in Markdown - rendering tests

[![NPM package](https://img.shields.io/npm/v/math-in-markdown-test.svg?style=flat)](https://www.npmjs.com/package/math-in-markdown-test)
[![MIT license](https://img.shields.io/badge/license-MIT-brightgreen.svg)](https://opensource.org/licenses/MIT)

This document tests math expression support in the Markdown renderers of
VS Code, GitHub, and npmjs.com.

## Simple Unicode

- Normal font (`√(x²+1)`) ⟶ √(x²+1)
- Italic (`_√(x²+1)_`) ⟶ _√(x²+1)_
- Bold (`**√(x²+1)**`) ⟶ **√(x²+1)**
- Code (`` `√(x²+1)` ``) ⟶ `√(x²+1)`
  
**Conclusion**: Works everywhere.

## HTML superscript

- `√(x<sup>2</sup>+1)` ⟶ √(x<sup>2</sup>+1)  

**Conclusion**: Works everywhere.

## R Markdown superscript

https://rmarkdown.rstudio.com/authoring_basics.html

- `√(x^2^+1)` ⟶ √(x^2^+1)

**Conclusion**: Proprietary syntax; unsupported by VS Code, GitHub, and npmjs.

## Inline equations (`$...$`)

- `$√(x²+1)$` ⟶ $√(x²+1)$
- `$\sqrt{x^2+1}$` ⟶ $\sqrt{x^2+1}$
- `$\frac{1}{2}$` ⟶ $\frac{1}{2}$
- `$ℚ \subset \mathbb{R}$` ⟶ $ℚ \subset \mathbb{R}$
- `$\begin{bmatrix}1 & 3\end{bmatrix}^T$` ⟶ $\begin{bmatrix}1 & 3\end{bmatrix}^T$

**Conclusion**: Simple expressions work in VS Code and GitHub with minor
vertical alignment issues on the latter. The way GitHub renders `\mathbb` works
in Safari but not in Chrome. It fails to parse complex formulae unless they're
between ````$` `$```` delimiters.

Discussion: [Stack Overflow](https://stackoverflow.com/questions/79433588/how-can-i-represent-mathbbcharacter-in-github-markdown)

## Inline equations, GitHub style (````$`...`$````)

https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions

- ````$`\sqrt{x²+1}`$```` ⟶ $`\sqrt{x²+1}`$
- ````$`ℚ \subset \mathbb{R}`$```` ⟶ $`ℚ \subset \mathbb{R}`$
- ````$`\begin{bmatrix}1 & 3\end{bmatrix}^T`$```` ⟶ $`\begin{bmatrix}1 & 3\end{bmatrix}^T`$

**Conclusion**: Works only on GitHub. VS Code renders the backticks literally.
npmjs does not support it at all.

## Block equations (`$$...$$`)

`$$\frac{x+1}{2}$$`

$$\frac{x+1}{2}$$

`$$ \frac{x+1}{2} $$`

$$ \frac{x+1}{2} $$

`$$\frac{x+1}{2}$$` (no blank line before expression)
$$\frac{x+1}{2}$$

**Conclusion**: Works in VS Code. On GitHub, a blank line is required before
the equation. Not supported on npmjs.

## Math blocks (<code>```math</code>)

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

**Conclusion:** Simple expressions render correctly in both VS Code and GitHub.
GitHub struggles with aligned equations.

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

**Conclusion**: Only works in VSCode.

## CodeCogs

The expressions below are SVGs created with the
[CodeCogs equation editor](https://editor.codecogs.com/) and embedded from
latex.codecogs.com.

- Inline formula: ![inline formula](https://latex.codecogs.com/svg.image?\inline&space;\sqrt{x^2&plus;1})
- Inline fraction: ![inline fraction](https://latex.codecogs.com/svg.image?\inline&space;\frac{1}{2})
- Vertical centering with `<span style="vertical-align: middle">`: <span style="vertical-align: middle">![inline fraction](https://latex.codecogs.com/svg.image?\inline&space;\frac{1}{2})</span>

**Conclusion**: Works, but vertical alignment is often off.
GitHub and npmjs don’t allow fine-tuning with CSS.
