**Use Bankers algorithms and explain if request for (1,0,0) by P2 can be granted?**
>available resources are(10, 5, 7) instances for  (A,B,C)

![](Pasted%20image%2020231208191340.png)
## Need = Max - Allocation

![](Pasted%20image%2020231208191603.png)
- #### If Request <= Need. (100 <= 600) True  ===> Then go to next step
- #### If Request <= Available, (100 <= 332) True ===> Then go to next step
- #### Pretend to allocate requested resources to `P2`:
	- ###### Available = Available - Request = `332 - 100 = 232` 
	- ###### Allocation = Allocation + Request = `302 + 100 = 402`
	- ###### Need = Need - Request = `600 - 100 = 500`
 
## New Table
![](Pasted%20image%2020231208191750.png)

- ###### Work = Available = (232)
- ###### Lets check `Need <= Work`
###### P1: 122 <= 232 ===> **True**, Work =   work + allocation P1 = 232 +200 = **432**
###### P3: 011 <= 432 ===> **True**, Work =   work + allocation P3 = 432 + 211 = **643**
###### P4: 431 <= 632 ===> **True**, Work =   work + allocation P4 = 643 + 002 = **645**
###### P2: 500 <= 645 ===> **True**, Work =   work + allocation P2 = 645 + 402 = **1047**
###### P0: 743 <= 1047 ===> **True**, Work =   work + allocation P0 = 1047 + 010 = **1057**

#### Safe Sequence = <P1, P3, P4, P2, P0>.
> A request for (1,0,0) by P2 can be granted. 
