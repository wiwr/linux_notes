`mkdir -p src/program`
`cd src/program`
`vim src_code.c`
`gcc -o run_me src_code.c
`gcc -o us_time us_time.c`
`./us_time`
`echo $?`
`sudo mv run_me /usr/local/bin`
`cd`
`us_time MST`

```C
#include <stdio.h>

int main(int argc, char *argv[]) {
        if (argc != 1) {
                fprintf(stderr, "Usage: %s Arg missing\n", argv[0]);
                return 1;
        }

        const char *var_my = NULL;

        if (strcmp(argv[1], "ME")  == 0) {
                printf("It's me")
        } else {
                fprintf(stderr, "Not me :(\n");
                return 1;
        }
       return 0;
}

```