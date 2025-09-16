# Math in Markdown rendering tests

Tests math expression support in the VSCode, GitHub and npmjs.com Markdown renderers

## Simple Unicode

- Normal (`√(x²+1)`) ⟶ √(x²+1)
- Italic (`_√(x²+1)_`) ⟶ _√(x²+1)_
- Bold (`**√(x²+1)**`) ⟶ **√(x²+1)**
- Code (`` `√(x²+1)` ``) ⟶ `√(x²+1)`
  
## HTML superscript

- `√(x<sup>2</sup>+1)` ⟶ √(x<sup>2</sup>+1)

## R Markdown superscript

https://rmarkdown.rstudio.com/authoring_basics.html

- `√(x^2^+1)` ⟶ √(x^2^+1)

## Inline equation (`$...$`)

- `$√(x²+1)$` ⟶ $√(x²+1)$
- `$√(x^2+1)$` ⟶ $√(x^2+1)$
- `$\sqrt{x²+1}$` ⟶ $\sqrt{x²+1}$
- `$\sqrt{x^2+1}$` ⟶ $\sqrt{x^2+1}$
- `$\frac{1}{2}$` ⟶ $\frac{1}{2}$

## Inline equation, GitHub style (````$`...`$````)

https://docs.github.com/en/get-started/writing-on-github/working-with-advanced-formatting/writing-mathematical-expressions

- ````$`\sqrt{x²+1}`$```` ⟶ $`\sqrt{x²+1}`$  
  As of Sep 2025 VSCode renders the backticks verbatim.

## Display equation (`$$...$$`)

`$$\frac{x+1}{2}$$`

$$\frac{x+1}{2}$$

`$$ \frac{x+1}{2} $$`

$$ \frac{x+1}{2} $$

`$$\frac{x+1}{2}$$` (no blank line before expression)
$$\frac{x+1}{2}$$

## Math block (<code>```math</code>)

````
```math
\sqrt{x^2+1}
```
````

```math
\sqrt{x^2+1}
```

### Aligned equations

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
