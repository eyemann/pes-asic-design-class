# pes_asic_class
# VLSI Physical Design for ASICs


<details>
  <summary>DAY 1 
	  Introduction to RISCV ISA and GNU Compiler Toolchain </summary>
  <br>



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
</br>
</details>

<details>
  <summary>DAY 2 
	  Introduction to ABI and Basic Verification Flow </summary>
  <br>

## C program using asm

<img width="547" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/0b9253d6-e44f-4d97-85c2-ef9e8f917a6f">

</details>

<details>
  <summary>DAY 3 
	  Introduction to Verilog RTL design and Synthesis </summary>
  <br>

## Using iverilog and gtkwave

+ `mkdir vsd`
+ `cd vsd`
+ `git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git`

+ `cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files`
+ `iverilog good_mux.v tb_good_mux.v`
+ `./a.out`
+ `gtkwave tb_good_mux.vcd `

+ `gvim tb_good_mux.v -o good_mux.v`
<img width="501" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/ae1a032d-db72-4915-a03c-aa9181951237">


<img width="562" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/9c1f455d-f405-4d68-9983-b319c2c0c588">



## Yosys and Logic Synthesis

+ `cd`
+ `cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files`
+  `yosys`

<img width="440" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/3c85e5c3-8e6f-4741-8ecf-866d0abab9d8">

<img width="579" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/21d8077f-645c-4c8a-80db-03fb0b15de0b">

+ ` read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+ `read_verilog good_mux.v`
+ `synth -top good_mux`

<img width="231" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/52fc8f6d-b3a2-484b-868a-ad850d08bceb">

</details>

<details>
  <summary>DAY 4
	 Introduction to Timing Dot Libs </summary>
  <br>
<details>
<summary> Introduction to Dot Lib </summary>	

<img width="399" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/8eaf117b-2507-4d27-9221-10989bb0d987">
</br>
</details>
<details>
<summary> Hierarchical Synthesis Flat Synthesis </summary>

 + `multiple_modules.v`

  - `cd vsd/sky130RTLDesignAndSynthesisWorkshop/verilog_files`
  -  `gvim multiple_modules.v`
     
<img width="439" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/ebe6fb60-3bfa-48ef-aeca-48e74da68bcc">

+  `multiple_modules` instantiates `sub_module1` and `sub_module2`

+  `yosys`
+  `read_liberty -lib ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+  ` read_verilog multiple_modules.v`
+  `synth -top multiple_modules` //to set it as top module

<img width="334" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/b1fed7f9-98e7-48c0-a913-883044ea134f">

+  `abc -liberty ../lib/sky130_fd_sc_hd__tt_025C_1v80.lib`
+  To view the netlist `show multiple_modules`
+ `write_verilog -noattr multiple_modules_hier.v`
+ `!gvim multiple_modules_hier.v`

<img width="287" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/a9f76084-bad6-40de-8286-b48a80bb503d">


<img width="343" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/d3b07264-134e-43c1-8728-129d1a1c9b6f">

</br>
</details>

<details>
<summary>D Flip-Flop with Asynchronous Reset</summary>	

 `gvim dff_asyncres_syncres.v`
 
<img width="466" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/1c9e7627-f173-4768-a384-26ce64f41fbe">
</br>
</details>

<details>
<summary>D Flip-Flop with Asynchronous set</summary>

`gvim dff_async_set.v`

<img width="455" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/2567b948-b71d-4e0e-ae86-b89a56e418e3">
</br>
</details>

<details>
<summary>D Flip-Flop with Synchronous Reset</summary>
	
`gvim dff_syncres.v`

<img width="445" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/a7efb63d-0fcf-4579-a5b8-dca6ce96c397">
</br>
</details>

<img width="604" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/f5237b95-4873-44d6-84bc-be0c81829477">


<img width="425" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/ae853aec-24cd-4abe-874e-9940533fde92">

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/492639f6-68b3-4950-ad40-bb69ece929ee)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/b4981944-78ab-4adb-8aaf-6776fa3ff9af)


![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/cefd4143-f4aa-4701-b4e2-e3fa62d8fed6)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/db472146-4699-4546-a4fc-fd8341e0e2dd)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/8e7f1387-1dd2-4279-89d3-ca7cb2fcca8e)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/7f9d57d2-9fb7-4c79-8e30-a7502a37196a)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/80f0dc8e-9f6b-4b9f-baf3-96239b461624)


![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/ca834a45-e19c-4f19-a66b-bf45e244f129)


![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/280caf21-0d82-4edc-a701-3a70a864836f)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/c0fb2bef-d3ad-4eb2-b7f9-525da00a2ca6)
</br>
</details>
</br>
</details>
<details>
  <summary>DAY 5 
	  Introduction to Optimisations </summary>
  <br>

<img width="421" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/e141bc3f-98da-456f-bd19-b003d6748394">

<img width="438" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/d80c4712-3155-42a6-9bda-93f4de9f22ae">

<img width="360" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/5f758fef-e5c6-4c0c-939d-ac49e0035046">

<img width="422" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/3f190693-40b6-472b-91d4-30baccfc3a04">

<img width="440" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/8be6d498-9ac8-4903-9e11-16cbab2ecb9d">

<img width="452" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/ff9490cd-0013-4364-97f6-a7ba4f6bbfd1">

<img width="386" alt="image" src="https://github.com/eyemann/pes-asic-design-class/assets/142375203/6f3692ff-8185-487b-9777-3ed75a54a5ba">

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/da65c9b1-0f55-443b-aea6-1b2bc0121de7)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/dc466c89-34c6-460a-84aa-a7a696e6aa52)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/dd6f958e-36e2-438e-92ae-223a0aaa84b2)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/e885e27b-095a-4bde-b59a-d51b3198039c)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/47863c26-7d87-420d-8144-047cbc096f5c)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/33d670b3-be75-48df-8dc6-3928c56095fa)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/4474e2da-a8f3-4380-b7c3-7197fd80b820)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/839fa475-bcaa-4cf1-8158-b2d4092e921c)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/6b450d9a-b688-4b7d-b3bd-55e6cf09c535)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/65fdc741-06de-46ae-afad-0f8c6ceb4ceb)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/52e9d53d-11a8-4c30-bf86-570e439e50cc)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/b16ca3c5-1176-4b06-9b26-8caf79ff97c3)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/461331d9-182d-4009-817a-748dbb433589)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/ec810ff9-8edb-474b-8ddb-74531db725c7)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/276cbe61-2dba-44fa-ba8c-40c691856bc8)

</br>
</details>

<details>
  <summary>DAY 6 
	 GLS Synthesis</summary>
  <br>

 ![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/514ead36-3132-4454-aaca-429e8d7ee4dc)

 ![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/66ecd35a-01ed-4582-8e1e-5004ceb75f77)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/94c8ecdc-6aef-4012-b1a5-b27fdfe6952f)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/34790038-329d-45c8-8352-01bd66a6dd8e)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/d3ce6344-9598-4639-9832-dc97359417b9)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/7f2e3fb6-4458-4eea-af72-9656ac5f862e)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/d45aae30-153f-4562-9f21-a37116c2b425)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/bea780a0-eb0a-4f61-8f98-6170242e3b75)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/2b0d53ca-0122-48d2-92dd-98c233188dce)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/9c1baef0-4879-4dd4-bce0-2fc3f23932aa)

![image](https://github.com/eyemann/pes-asic-design-class/assets/142375203/12a99db3-8027-428d-8e3b-94052a15bf6d)

 </br>
</details>
