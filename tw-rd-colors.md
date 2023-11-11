# Replacing Tailwind color palette with Radix Colors

Radix Colors automatic dark mode colors can be overwritten with the `dark` Tailwind variant (?)

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

function radixColors(name) {
  let scale = Array.from({ length: 12 }, (_, i) => {
    let id = i + 1;
    return [
      [id, `var(--${name}${id})`],
      [`a${id}`, `var(--${name}A${id})`],
    ];
  }).flat();

  return Object.fromEntries(scale);
}
```

\+ purge unused variables?
