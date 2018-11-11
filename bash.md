# Bash

***

## String

### String Length

```bash
${#string}
```

### Substring in string

```bash
if [[ "$string" == *"$substring"* ]]; then
    echo "'$string' contains '$substring'";
else
    echo "'$string' does not contain '$substring'";
fi
```

### Substring Extraction

```bash
${string:position}
```

```bash
${string:position:length}
```

### Substring Removal

```bash
${string#substring}
```

> Deletes **shortest** match of \$substring from **front** of \$string.

```bash
${string##substring}
```

> Deletes **longest** match of \$substring from **front** of \$string.

```bash
${string%substring}
```

> Deletes **shortest** match of \$substring from **back** of \$string.

```bash
${string%%substring}
```

> Deletes **longest** match of \$substring from **back** of \$string.

### Substring Replacement

```bash
${string/substring/replacement}
```

> Replace **first** match of \$substring with \$replacement.

```bash
${string//substring/replacement}
```

> Replace **all** matches of \$substring with \$replacement.

```bash
${string/#substring/replacement}
```

> If \$substring matches **front end** of \$string, substitute \$replacement for \$substring.

```bash
${string/%substring/replacement}
```

> If \$substring matches **back end** of \$string, substitute \$replacement for \$substring.


