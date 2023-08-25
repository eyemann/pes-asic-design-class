# pes_asic_class

# VLSI Physical Design for ASICs
## Objective


<img width="399" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/f6d007e4-e06a-4ac6-aec8-10f4acb8b104">




`leafpad sumton.c`
``` c
#include<stdio.h>

int main(){
	int i, sum=0, n=111;
	for (i=1;i<=n; ++i) {
	sum +=i;
	}
	printf("Sum of numbers from 1 to %d is %d \n",n,sum);
	return 0;
}
```
<img width="357" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/5327bec5-1fea-4d43-96fd-7722ea5fe1d9">


`gcc sumton.c`
`.\a.out`


<img width="364" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/419de06a-2e73-4cd8-b899-18065f55aa6c">



## Spike Simulation and Debug

`spike pk sum1ton.o` -> to check whether the instructions produced are right to give the correct output.

<img width="372" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/5f13854e-2764-4e2c-b1dd-86c3f564c973">



`spike -d pk sum1ton.c` is used for debugging.

 Positive : [0 , 2^(n-1)-1]
          Negative : [-1 to 2^(n-1)]

## Labwork

<img width="445" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/c333edb6-c455-451e-8b82-39568087e11a">
```

<img width="420" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/ca7f0384-598d-4d81-96d4-5b583b6198b0">


