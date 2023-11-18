# Replacing Tailwind colors with Radix Colors in Next.js

Caveat: PurgeCSS can't purge unused imported css variables. Workaround: script to write variables in global.css? or copy source css files into app?

## 1) Install dependencies for custom PostCSS/PurgeCSS management

```
npm i -D postcss-flexbugs-fixes postcss-preset-env @fullhuman/postcss-purgecss @radix-ui/colors
```

## 2) Replace `postcss.config.js` content

```
module.exports = {
  plugins:
    process.env.NODE_ENV === "production"
      ? [
          "tailwindcss",
          "postcss-flexbugs-fixes",
          [
            "postcss-preset-env",
            {
              autoprefixer: {
                flexbox: "no-2009",
              },
              stage: 3,
              features: {
                "custom-properties": false,
              },
            },
          ],
          [
            "@fullhuman/postcss-purgecss",
            {
              content: [
                "./pages/**/*.{js,jsx,ts,tsx}",
                "./app/**/*.{js,jsx,ts,tsx}",
                "./components/**/*.{js,jsx,ts,tsx}",
              ],
              css: [
                "./pages/**/*.css",
                "./app/**/*.css",
                "./components/**/*.css",
              ],
              variables: true,
              defaultExtractor: (content) =>
                content.match(/[\w-/:]+(?<!:)/g) || [],
              safelist: ["html", "body"],
            },
          ],
        ]
      : ["tailwindcss"],
}
```

## 3) Import Radix Colors in `global.css` after `@tailwind` declarations

```
@import "@radix-ui/colors/gray.css";
@import "@radix-ui/colors/grayA.css";
@import "@radix-ui/colors/grayDark.css";
@import "@radix-ui/colors/grayDarkA.css";
@import "@radix-ui/colors/tomato.css";
@import "@radix-ui/colors/tomatoA.css";
@import "@radix-ui/colors/tomatoDark.css";
@import "@radix-ui/colors/tomatoDarkA.css";
@import "@radix-ui/colors/red.css";
@import "@radix-ui/colors/redA.css";
@import "@radix-ui/colors/redDark.css";
@import "@radix-ui/colors/redDarkA.css";
@import "@radix-ui/colors/ruby.css";
@import "@radix-ui/colors/rubyA.css";
@import "@radix-ui/colors/rubyDark.css";
@import "@radix-ui/colors/rubyDarkA.css";
@import "@radix-ui/colors/crimson.css";
@import "@radix-ui/colors/crimsonA.css";
@import "@radix-ui/colors/crimsonDark.css";
@import "@radix-ui/colors/crimsonDarkA.css";
@import "@radix-ui/colors/pink.css";
@import "@radix-ui/colors/pinkA.css";
@import "@radix-ui/colors/pinkDark.css";
@import "@radix-ui/colors/pinkDarkA.css";
@import "@radix-ui/colors/plum.css";
@import "@radix-ui/colors/plumA.css";
@import "@radix-ui/colors/plumDark.css";
@import "@radix-ui/colors/plumDarkA.css";
@import "@radix-ui/colors/purple.css";
@import "@radix-ui/colors/purpleA.css";
@import "@radix-ui/colors/purpleDark.css";
@import "@radix-ui/colors/purpleDarkA.css";
@import "@radix-ui/colors/violet.css";
@import "@radix-ui/colors/violetA.css";
@import "@radix-ui/colors/violetDark.css";
@import "@radix-ui/colors/violetDarkA.css";
@import "@radix-ui/colors/iris.css";
@import "@radix-ui/colors/irisA.css";
@import "@radix-ui/colors/irisDark.css";
@import "@radix-ui/colors/irisDarkA.css";
@import "@radix-ui/colors/indigo.css";
@import "@radix-ui/colors/indigoA.css";
@import "@radix-ui/colors/indigoDark.css";
@import "@radix-ui/colors/indigoDarkA.css";
@import "@radix-ui/colors/blue.css";
@import "@radix-ui/colors/blueA.css";
@import "@radix-ui/colors/blueDark.css";
@import "@radix-ui/colors/blueDarkA.css";
@import "@radix-ui/colors/cyan.css";
@import "@radix-ui/colors/cyanA.css";
@import "@radix-ui/colors/cyanDark.css";
@import "@radix-ui/colors/cyanDarkA.css";
@import "@radix-ui/colors/teal.css";
@import "@radix-ui/colors/tealA.css";
@import "@radix-ui/colors/tealDark.css";
@import "@radix-ui/colors/tealDarkA.css";
@import "@radix-ui/colors/jade.css";
@import "@radix-ui/colors/jadeA.css";
@import "@radix-ui/colors/jadeDark.css";
@import "@radix-ui/colors/jadeDarkA.css";
@import "@radix-ui/colors/green.css";
@import "@radix-ui/colors/greenA.css";
@import "@radix-ui/colors/greenDark.css";
@import "@radix-ui/colors/greenDarkA.css";
@import "@radix-ui/colors/grass.css";
@import "@radix-ui/colors/grassA.css";
@import "@radix-ui/colors/grassDark.css";
@import "@radix-ui/colors/grassDarkA.css";
@import "@radix-ui/colors/brown.css";
@import "@radix-ui/colors/brownA.css";
@import "@radix-ui/colors/brownDark.css";
@import "@radix-ui/colors/brownDarkA.css";
@import "@radix-ui/colors/bronze.css";
@import "@radix-ui/colors/bronzeA.css";
@import "@radix-ui/colors/bronzeDark.css";
@import "@radix-ui/colors/bronzeDarkA.css";
@import "@radix-ui/colors/gold.css";
@import "@radix-ui/colors/goldA.css";
@import "@radix-ui/colors/goldDark.css";
@import "@radix-ui/colors/goldDarkA.css";
@import "@radix-ui/colors/sky.css";
@import "@radix-ui/colors/skyA.css";
@import "@radix-ui/colors/skyDark.css";
@import "@radix-ui/colors/skyDarkA.css";
@import "@radix-ui/colors/mint.css";
@import "@radix-ui/colors/mintA.css";
@import "@radix-ui/colors/mintDark.css";
@import "@radix-ui/colors/mintDarkA.css";
@import "@radix-ui/colors/lime.css";
@import "@radix-ui/colors/limeA.css";
@import "@radix-ui/colors/limeDark.css";
@import "@radix-ui/colors/limeDarkA.css";
@import "@radix-ui/colors/yellow.css";
@import "@radix-ui/colors/yellowA.css";
@import "@radix-ui/colors/yellowDark.css";
@import "@radix-ui/colors/yellowDarkA.css";
@import "@radix-ui/colors/amber.css";
@import "@radix-ui/colors/amberA.css";
@import "@radix-ui/colors/amberDark.css";
@import "@radix-ui/colors/amberDarkA.css";
@import "@radix-ui/colors/orange.css";
@import "@radix-ui/colors/orangeA.css";
@import "@radix-ui/colors/orangeDark.css";
@import "@radix-ui/colors/orangeDarkA.css";
```

## 4) Add `radixColors` function in `tailwind.config.ts`

```
function radixColors(color) {
  let scale = Array.from({ length: 12 }, (_, i) => {
    let id = i + 1;
    return [
      [id, `var(--${color}${id})`],
      [`a${id}`, `var(--${color}A${id})`],
    ];
  }).flat();

  return Object.fromEntries(scale);
}
```

## 5) Add `colors` in `theme` of `tailwind.config.ts`

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