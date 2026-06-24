base on  https://curse.ysap.sh
```bash
#!/usr/bin/env bash

i=2

my-func() {
	i=6
	echo hi
}

thing=${ my-func; }
echo "thing is $thing"
echo "i is $i"
```