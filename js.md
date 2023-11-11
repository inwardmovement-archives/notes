# LOGIQUE

```
si && alors                    (renvoie le premier falsy, ou le dernier truthy)
si || sinon                    (renvoie le premier truthy, ou le dernier falsy)
si null_ou_undefined ?? alors  (renvoie le premier non nullish, ou le dernier nullish) (valeur par défaut)

si &&= alors prend la valeur
si ||= sinon prend la valeur
si null_ou_undefined ??= alors prend la valeur

truthy : [], {}
falsy : 0, "", null, undefined

!! convertit une valeur dans le bolléen correspondant
```

# RE

- les métacaractères (ex : .) sont des caractères normaux dans []
- ? = aussi peu de fois que possible
- [\s\S] = n'importe quel caractère (absolu, tout type d'espace inclus)

# DOM

```
const el = document.querySelector()
// document.querySelectorAll()
const newEl = document.createElement("p")
newEl.innerHTML = ""
// el.append(newEl)
// el.prepend(newEl)
el.insertAdjacentElement("beforebegin", newEl)
// el.insertAdjacentHTML("beforebegin", newEl)
el.nextElementSibling
el.parentElement
el.firstElementChild
el.childElementCount
el.remove()
el.append(newEl.cloneNode(true))
```