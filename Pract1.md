## Task 1

```
grep -v '^#' /etc/passwd | cut -d: -f1 | sort
```

## Task 2

```
grep -v '^#' /etc/protocols | awk '{print $2, $1}' | sort -nr | head -5
```

## Task 3

```
nano banner

#!/bin/bash

text="$*"
length=${#text}
width=$((length + 2))

printf '+%*s+\n' "$width" '' | tr ' ' '-'
printf '| %s |\n' "$text"
printf '+%*s+\n' "$width" '' | tr ' ' '-'

chmod +x banner

./banner "Hello from RTU MIREA!"
```

## Task 4 

```
nano identifiers

#!/bin/bash

if [ -z "$1" ]; then
    echo "Usage: $0 <file>"
    exit 1
fi

grep -Eo '[A-Za-z_][A-Za-z0-9_]*' "$1" | sort -u | tr '\n' ' '
echo

chmod +x identifiers

./identifiers hello.c
```

## Task 5

```
nano reg

#!/bin/bash

if [ -z "$1" ]; then
    echo "Usage: $0 <program>"
    exit 1
fi

chmod +x "$1"
cp "$1" /usr/local/bin/
chmod 755 "/usr/local/bin/$1"

echo "$1 registered successfully"

chmod +x reg

./reg banner

banner "Hello"
```

## Task 6

```


```

## Task 7

```

```

## Task 8

```

```

## Task 9

```

```

## Task 10

```

```
