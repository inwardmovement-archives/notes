# Replacing Tailwind color palette with Radix Colors

Notes:
- Ignore black/white alpha colors, use Tailwind black/white with opacity modifier instead.
- Purge unused variables?

```
npm i @radix-ui/colors
```

style.css:
```
@import "@radix-ui/colors/*.css";
```

tailwind.config.js:
```
...
  theme: {
    colors: {
      black: "rgb(0 0 0)",
      white: "rgb(255 255 255)",
      inherit: "inherit",
      transparent: "transparent",
      current: "currentColor",
      gray: radixColors("gray"),
      ...
    },
  },
...

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
