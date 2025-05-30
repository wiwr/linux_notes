Calculate previous month and correct year for that month.
### Bash script
```bash
#!/bin/bash
# Get current month and year
current_month=$(date +%m)
current_year=$(date +%Y)

# Remove leading zero
current_month=$((10#$current_month))

# Calculate previous month
if [ "$current_month" -eq 1 ]; then
	previous_month=12
	previous_year=$((current_year -1))
else
	previous_month=$(printf "%02d" $((current_month -1)))
	previous_year=$current_year
fi

# Present result
echo "Previous month: $previous_month"
echo "Year: $previous_year"
```

### Bash function
```bash
get_previous_month_and_year() {
	local current_month current_year previous_month previous_year
	
	# Get current month and year
	current_month=$(date +%m)
	current_year=$(date +%Y)

	# Remove leading zero
	current_month=$((10#$current_month))

	# Calculate previous month
	if [ "$current_month" -eq 1 ]; then
		previous_month=12
		previous_year=$((current_year -1))
	else
		previous_month=$(printf "%02d" $((current_month -1)))
		previous_year=$current_year
	fi

	# Return results
	echo "$previous_year $previous_month"
}
```

```bash
read prev_month prev_year < <(get_previous_month_and_year)
echo "Previous month: $prev_month"
echo "Year: $prev_year"
```
### Comments
* using `10#$var_name` to avoid octal interpretation
* `"%02d"`for `printf` is used to get two digit number with leading zeros when needed. Examples:
	* `printf %03d $counter`
	* ```mv $a `printf %04d.%s ${a%.*} $(a##*.}` ```