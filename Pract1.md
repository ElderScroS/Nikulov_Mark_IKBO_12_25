#Practice

## Task 1

```
#!/bin/bash  text="$*" length=${#text} width=$((length + 2))  printf '+%*s+\n' "$width" '' | tr ' ' '-' printf '| %s |\n' "$text" printf '+%*s+\n' "$width" '' | tr ' ' '-'
```

