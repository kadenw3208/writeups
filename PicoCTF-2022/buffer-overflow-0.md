# buffer-overflow-0
Category: Binary Exploitation
Points: 100
## Problem Description
Smash the stack<br>Let's start off simple, can you overflow the correct buffer? The program is available  [here](https://artifacts.picoctf.net/c/173/vuln). You can view source  [here](https://artifacts.picoctf.net/c/173/vuln.c). And connect with it using:`nc saturn.picoctf.net 51532`
## Writeup
After viewing the source code, this is what we get
```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <signal.h>

#define FLAGSIZE_MAX 64

char flag[FLAGSIZE_MAX];

void sigsegv_handler(int sig) {
  printf("%s\n", flag);
  fflush(stdout);
  exit(1);
}

void vuln(char *input){
  char buf2[16];
  strcpy(buf2, input);
}

int main(int argc, char **argv){
  
  FILE *f = fopen("flag.txt","r");
  if (f == NULL) {
    printf("%s %s", "Please create 'flag.txt' in this directory with your",
                    "own debugging flag.\n");
    exit(0);
  }
  
  fgets(flag,FLAGSIZE_MAX,f);
  signal(SIGSEGV, sigsegv_handler); // Set up signal handler
  
  gid_t gid = getegid();
  setresgid(gid, gid, gid);


  printf("Input: ");
  fflush(stdout);
  char buf1[100];
  gets(buf1); 
  vuln(buf1);
  printf("The program will exit now\n");
  return 0;
}
```
Sincce `sigsev_handler` is the function that prints the flag, we can safely assume that we have to cause a segmentation fault. We can just input a long string of characters to get the flag and overflow the function.
<br>`picoCTF{ov3rfl0ws_ar3nt_that_bad_90d2bb58}`
