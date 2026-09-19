## Task 1

```
grep -v '^#' /etc/passwd | cut -d: -f1 | sort
```

## Task 2

```
grep -v '^#' /etc/protocols | awk '{print $2, $1}' | sort -nr | head -5
```

## Task 3

```bash
nano banner
```

```bash
#!/bin/bash

text="$*"
length=${#text}
width=$((length + 2))

printf '+%*s+\n' "$width" '' | tr ' ' '-'
printf '| %s |\n' "$text"
printf '+%*s+\n' "$width" '' | tr ' ' '-'
```

```bash
chmod +x banner

./banner "Hello from RTU MIREA!"
```

## Task 4

```bash
nano identifiers
```

```bash
#!/bin/bash

if [ -z "$1" ]; then
    echo "Usage: $0 <file>"
    exit 1
fi

grep -Eo '[A-Za-z_][A-Za-z0-9_]*' "$1" | sort -u | tr '\n' ' '
echo
```

```bash
chmod +x identifiers

./identifiers hello.c
```

## Task 5

```bash
nano reg
```

```bash
#!/bin/bash

if [ -z "$1" ]; then
    echo "Usage: $0 <program>"
    exit 1
fi

chmod +x "$1"
cp "$1" /usr/local/bin/
chmod 755 "/usr/local/bin/$1"

echo "$1 registered successfully"
```

```bash
chmod +x reg

./reg banner

banner "Hello"
```

## Task 6

```bash
nano check_comments
```

```bash
#!/bin/bash

find . -type f \( -name "*.c" -o -name "*.js" -o -name "*.py" \) -exec awk 'NR==1 && ($0 ~ /^[[:space:]]*\/\// || $0 ~ /^[[:space:]]*#/ || $0 ~ /^[[:space:]]*\/\*/) {print FILENAME}' {} \;
```

```bash
chmod +x check_comments

./check_comments
```

## Task 7

```bash
nano duplicates
```

```bash
#!/bin/bash

if [ -z "$1" ]; then
    echo "Usage: $0 <directory>"
    exit 1
fi

find "$1" -type f -exec md5sum {} + | sort | awk '
{
    if ($1 == prev) {
        print prev_file
        print $2
    }
    prev=$1
    prev_file=$2
}'
```

```bash
chmod +x duplicates

./duplicates .
```

## Task 8

```bash
nano archive
```

```bash
#!/bin/bash

if [ -z "$1" ]; then
    echo "Usage: $0 <extension>"
    exit 1
fi

find . -maxdepth 1 -type f -name "*.$1" -print0 | tar --null -cf archive.tar --files-from=-
```

```bash
chmod +x archive

./archive c
```

## Task 9

```bash
nano spaces_to_tabs
```

```bash
#!/bin/bash

if [ $# -ne 2 ]; then
    echo "Usage: $0 <input> <output>"
    exit 1
fi

sed 's/    /\t/g' "$1" > "$2"
```

```bash
chmod +x spaces_to_tabs

./spaces_to_tabs input.txt output.txt
```

## Task 10

```bash
nano empty_files
```

```bash
#!/bin/bash

if [ -z "$1" ]; then
    echo "Usage: $0 <directory>"
    exit 1
fi

find "$1" -type f -empty -print
```

```bash
chmod +x empty_files

./empty_files .
```
