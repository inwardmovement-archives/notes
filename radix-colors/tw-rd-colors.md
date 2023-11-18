# Replacing Tailwind colors with Radix Colors in Next.js

Caveat: unused css variables cannot be purged. Instead use https://github.com/mrcaidev/tailwindcss-radix-colors (but no automatic dark mode support).

## 1) Install Radix Colors

```
npm i -D @radix-ui/colors
```

## 2) Import Radix Colors in `global.css` after `@tailwind` declarations

```
@import "@radix-ui/colors/gray.css";
@import "@radix-ui/colors/gray-alpha.css";
@import "@radix-ui/colors/gray-dark.css";
@import "@radix-ui/colors/gray-dark-alpha.css";
@import "@radix-ui/colors/tomato.css";
@import "@radix-ui/colors/tomato-alpha.css";
@import "@radix-ui/colors/tomato-dark.css";
@import "@radix-ui/colors/tomato-dark-alpha.css";
@import "@radix-ui/colors/red.css";
@import "@radix-ui/colors/red-alpha.css";
@import "@radix-ui/colors/red-dark.css";
@import "@radix-ui/colors/red-dark-alpha.css";
@import "@radix-ui/colors/ruby.css";
@import "@radix-ui/colors/ruby-alpha.css";
@import "@radix-ui/colors/ruby-dark.css";
@import "@radix-ui/colors/ruby-dark-alpha.css";
@import "@radix-ui/colors/crimson.css";
@import "@radix-ui/colors/crimson-alpha.css";
@import "@radix-ui/colors/crimson-dark.css";
@import "@radix-ui/colors/crimson-dark-alpha.css";
@import "@radix-ui/colors/pink.css";
@import "@radix-ui/colors/pink-alpha.css";
@import "@radix-ui/colors/pink-dark.css";
@import "@radix-ui/colors/pink-dark-alpha.css";
@import "@radix-ui/colors/plum.css";
@import "@radix-ui/colors/plum-alpha.css";
@import "@radix-ui/colors/plum-dark.css";
@import "@radix-ui/colors/plum-dark-alpha.css";
@import "@radix-ui/colors/purple.css";
@import "@radix-ui/colors/purple-alpha.css";
@import "@radix-ui/colors/purple-dark.css";
@import "@radix-ui/colors/purple-dark-alpha.css";
@import "@radix-ui/colors/violet.css";
@import "@radix-ui/colors/violet-alpha.css";
@import "@radix-ui/colors/violet-dark.css";
@import "@radix-ui/colors/violet-dark-alpha.css";
@import "@radix-ui/colors/iris.css";
@import "@radix-ui/colors/iris-alpha.css";
@import "@radix-ui/colors/iris-dark.css";
@import "@radix-ui/colors/iris-dark-alpha.css";
@import "@radix-ui/colors/indigo.css";
@import "@radix-ui/colors/indigo-alpha.css";
@import "@radix-ui/colors/indigo-dark.css";
@import "@radix-ui/colors/indigo-dark-alpha.css";
@import "@radix-ui/colors/blue.css";
@import "@radix-ui/colors/blue-alpha.css";
@import "@radix-ui/colors/blue-dark.css";
@import "@radix-ui/colors/blue-dark-alpha.css";
@import "@radix-ui/colors/cyan.css";
@import "@radix-ui/colors/cyan-alpha.css";
@import "@radix-ui/colors/cyan-dark.css";
@import "@radix-ui/colors/cyan-dark-alpha.css";
@import "@radix-ui/colors/teal.css";
@import "@radix-ui/colors/teal-alpha.css";
@import "@radix-ui/colors/teal-dark.css";
@import "@radix-ui/colors/teal-dark-alpha.css";
@import "@radix-ui/colors/jade.css";
@import "@radix-ui/colors/jade-alpha.css";
@import "@radix-ui/colors/jade-dark.css";
@import "@radix-ui/colors/jade-dark-alpha.css";
@import "@radix-ui/colors/green.css";
@import "@radix-ui/colors/green-alpha.css";
@import "@radix-ui/colors/green-dark.css";
@import "@radix-ui/colors/green-dark-alpha.css";
@import "@radix-ui/colors/grass.css";
@import "@radix-ui/colors/grass-alpha.css";
@import "@radix-ui/colors/grass-dark.css";
@import "@radix-ui/colors/grass-dark-alpha.css";
@import "@radix-ui/colors/brown.css";
@import "@radix-ui/colors/brown-alpha.css";
@import "@radix-ui/colors/brown-dark.css";
@import "@radix-ui/colors/brown-dark-alpha.css";
@import "@radix-ui/colors/bronze.css";
@import "@radix-ui/colors/bronze-alpha.css";
@import "@radix-ui/colors/bronze-dark.css";
@import "@radix-ui/colors/bronze-dark-alpha.css";
@import "@radix-ui/colors/gold.css";
@import "@radix-ui/colors/gold-alpha.css";
@import "@radix-ui/colors/gold-dark.css";
@import "@radix-ui/colors/gold-dark-alpha.css";
@import "@radix-ui/colors/sky.css";
@import "@radix-ui/colors/sky-alpha.css";
@import "@radix-ui/colors/sky-dark.css";
@import "@radix-ui/colors/sky-dark-alpha.css";
@import "@radix-ui/colors/mint.css";
@import "@radix-ui/colors/mint-alpha.css";
@import "@radix-ui/colors/mint-dark.css";
@import "@radix-ui/colors/mint-dark-alpha.css";
@import "@radix-ui/colors/lime.css";
@import "@radix-ui/colors/lime-alpha.css";
@import "@radix-ui/colors/lime-dark.css";
@import "@radix-ui/colors/lime-dark-alpha.css";
@import "@radix-ui/colors/yellow.css";
@import "@radix-ui/colors/yellow-alpha.css";
@import "@radix-ui/colors/yellow-dark.css";
@import "@radix-ui/colors/yellow-dark-alpha.css";
@import "@radix-ui/colors/amber.css";
@import "@radix-ui/colors/amber-alpha.css";
@import "@radix-ui/colors/amber-dark.css";
@import "@radix-ui/colors/amber-dark-alpha.css";
@import "@radix-ui/colors/orange.css";
@import "@radix-ui/colors/orange-alpha.css";
@import "@radix-ui/colors/orange-dark.css";
@import "@radix-ui/colors/orange-dark-alpha.css";
```

## 3) Add `radixColors` function in `tailwind.config.ts`

```
function radixColors(color: string) {
  let scale = Array.from({ length: 12 }, (_, i) => {
    let id = i + 1;
    return [
      [id, `var(--${color}-${id})`],
      [`a${id}`, `var(--${color}-a${id})`],
    ];
  }).flat();

  return Object.fromEntries(scale);
}
```

## 4) Add `colors` in `theme` of `tailwind.config.ts`

```
colors: {
  black: "rgb(0 0 0)",
  white: "rgb(255 255 255)",
  inherit: "inherit",
  transparent: "transparent",
  current: "currentColor",
  gray: radixColors("gray"),
  tomato: radixColors("tomato"),
  red: radixColors("red"),
  ruby: radixColors("ruby"),
  crimson: radixColors("crimson"),
  pink: radixColors("pink"),
  plum: radixColors("plum"),
  purple: radixColors("purple"),
  violet: radixColors("violet"),
  iris: radixColors("iris"),
  indigo: radixColors("indigo"),
  blue: radixColors("blue"),
  cyan: radixColors("cyan"),
  teal: radixColors("teal"),
  jade: radixColors("jade"),
  green: radixColors("green"),
  grass: radixColors("grass"),
  brown: radixColors("brown"),
  bronze: radixColors("bronze"),
  gold: radixColors("gold"),
  sky: radixColors("sky"),
  mint: radixColors("mint"),
  lime: radixColors("lime"),
  yellow: radixColors("yellow"),
  amber: radixColors("amber"),
  orange: radixColors("orange"),
},
```
