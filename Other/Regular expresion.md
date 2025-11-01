`[dhp]og`, `[cf]an`

`^(\+\d{1,2}\s)?\(?\d{3}\)?[\s.-]\d{3}[\.-]\d{4}` = + 1 555 555 5555
`[0-9]{3}-[0-9]{3}-[0-9]{4}`
`^(?=.*[A-Za-z])(?=.*\d) [A-Za-z\d]{14,}$` 

##### nice
`^([a-zA-Z0-9_\-\.]+)@([a-zA-Z0-9_\-\.+)\.([a-zA-Z]{2,5})$` = email@example.com
##### poor
^\w*@\w*\.\w*$ = email@example.com


i### abbrevietion
`\d` = `[0-9]`
`\w` = `[a-zA-Z0-9_]`
`\s` = `[ \t\n\r\f]`

###  negation
`\D` = `[^0-9]`
`\W` = `[^a-zA-Z0-9_]`
`\S` = `[^ \t\n\r\f]`

`^ca` = car, cattle, canine
`ing$` = floating, sailing
`^cat$` = cat

## regex for grep
```bash
grep "c.t" /usr/share/dict/words
```

```bash
grep "c[aeiou]t" /usr/share/dict/words
```


