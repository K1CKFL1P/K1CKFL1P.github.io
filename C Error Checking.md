Back to [[C Programming Reference]]
# C Error Checking

There are a couple of useful methods to error check in C.

One way is to continuously prompt the user for an input **while** the input is undesirable
i.e.
```c
scanf("&d", &val);
while(val<0){
printf("Cannot enter negative numbers, try again");
scanf("%d", &val);
}
```

BUT what if the user enters a float, when the programmer is desiring an integer value???

In this case, we can assign `scanf()` to a variable.  `scanf()` holds a value that is equivalent to the amount of stuff that it scanned in from the user.  So if the programmer wanted a `%d` and the user inputs a `%f` , then we can use this to error check.

When combining this with a way to *clear the scan buffer*, we get powerful advanced error checking
i.e.

```c
numscanned = scanf("%d", &val);
while(numscanned == 0){ //check if scan successful

while(getchar()!='\n'); //clear the bad input

printf("Input error. Please try again.");

printf("How many values would you like to enter?");

numscanned = scanf("%d", &val) //update
}
```

notice the string of code: `while(getchar()!='\n')`
this is used to "*Clear the Buffer*" and allow for new user input
