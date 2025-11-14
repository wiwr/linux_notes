```bash
cat > text.txt
```

```bash
cat text.txt
```

```bash
cat >> text.txt
```

That will replace variables with values
```bash
cat << EOF
> Line with home directory $HOME
> Line with Path $PATH
> Line 3
> EOF
```

That will literally display text
```bash
cat << 'EOF'
> Line with $HOME
> EOF
```