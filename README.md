# pes_asic_class

# VLSI Physical Design for ASICs



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

## C program to show the maximum and minimum values of 64bit unsigned and signed numbers


<img width="445" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/c333edb6-c455-451e-8b82-39568087e11a">

  
<img width="469" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/473cddd0-660d-46f9-887e-b685dfc77887">

## C program using asm

<img width="547" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/0b9253d6-e44f-4d97-85c2-ef9e8f917a6f">

# Day 3


<img width="501" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/ae1a032d-db72-4915-a03c-aa9181951237">


<img width="562" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/9c1f455d-f405-4d68-9983-b319c2c0c588">

<img width="440" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/3c85e5c3-8e6f-4741-8ecf-866d0abab9d8">


<img width="579" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/21d8077f-645c-4c8a-80db-03fb0b15de0b">



<img width="231" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/52fc8f6d-b3a2-484b-868a-ad850d08bceb">


<img width="399" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/8eaf117b-2507-4d27-9221-10989bb0d987">


<img width="439" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/ebe6fb60-3bfa-48ef-aeca-48e74da68bcc">


<img width="334" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/b1fed7f9-98e7-48c0-a913-883044ea134f">


<img width="287" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/a9f76084-bad6-40de-8286-b48a80bb503d">


<img width="343" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/d3b07264-134e-43c1-8728-129d1a1c9b6f">


<img width="466" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/1c9e7627-f173-4768-a384-26ce64f41fbe">


<img width="455" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/2567b948-b71d-4e0e-ae86-b89a56e418e3">


<img width="445" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/a7efb63d-0fcf-4579-a5b8-dca6ce96c397">


<img width="604" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/f5237b95-4873-44d6-84bc-be0c81829477">
