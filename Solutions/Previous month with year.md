Calculate previous month and correct year for that month.
### Bash script
```bash
#!/bin/bash
# Get current month and year
current_month=$(date +%m)
current_year=$(date +%Y)

# Calculate previous month
if [ "$current_month" -eq 1 ]; then
	previous_month=12
	previous_year=$((current_year -1))
else
	previous_month=$(printf "%02d" $((10#$current_mont -1)))
	previous_year=$current_year
fi

# Present result
echo "Previous month: $previous_month"
echo "Year: $previous_year"
```

### Comments
* using `10#$var_name` to avoid octal interpretation
* `"%02d"`for `printf` is used to get two digit number with leading zeros when needed