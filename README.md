# Written questions:
## Q1

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


---------------------------------------------

## Q2
 **Given six memory partitions of 100 MB, 170 MB, 40 MB, 205 MB, 300 MB, and 185 MB (in order), how would the first-fit,best-fit, and worst-fit algorithms place processes of size 200 MB, 15 MB, 185 MB, 75 MB, 175 MB, and 80 MB (in order)? Indicate which—if any—requests cannot be satisfied. Comment on how efficiently each of the algorithms manages memory regarding internal or external fragmentation.**

(partitions) F = [100, 170, 40, 205, 300, 185]
(processes) P = [200, 15 , 185, 75, 175, 80] 
### First-fit:
- P[0] = 200 --> F[3] = 200 - 205 = 5
update:
Fs = [85, 170, 40, 5, 300, 185]

- P[1] = 15 --> F[0] = 100 - 15 = 85
update:
Fs = [85, 170, 40, 5, 300, 185]

- P[2] = 185 --> F[5] = 300 - 185 = 115
update:
Fs = [85, 170, 40, 5, 115, 185]

- P[3] = 75 --> F[0] = 85 - 75 = 10
update:
Fs = [10, 170, 40, 5, 115, 185]

- P[4] = 175--> F[5] = 185 - 175 = 10
update:
Fs = [10, 170, 40, 5, 115, 10]

- P[5] = 80 --> F[1] = 170 - 80 = 90
update:
Fs = [10, 90, 40, 5, 115, 10]

> First Fit is faster because it searches less but may be leave unused memory partitions leading to external fragmentation. 

### Best-fit:
(partitions) F = [100, 170, 40, 205, 300, 185]
(processes) P = [200, 15 , 185, 75, 175, 80] 

- P[0] = 200 --> F[3] = 200 - 205 = 5
update:
Fs = [100, 170, 40, 5, 300, 185]

- P[1] = 15 --> F[2] = 40 - 15 = 25
update:
Fs = [100, 170, 25, 5, 300, 185]

- P[2] = 185 --> F[5] = 185 - 185 = 0
update:
Fs = [100, 170, 25, 5, 300, 0]

- P[3] = 75 --> F[0] = 100 - 75 = 25
update:
Fs = [25, 170, 25, 5, 300, 0]

- P[4] = 175 --> F[4] = 300 - 175 = 125
update:
Fs = [25, 170, 25, 5, 125, 0]

- P[5] = 80 --> F[5] = 125 - 80 = 45
update:
Fs = [25, 170, 25, 5, 45, 0]

> Best fit may produce smallest leftover memory partitions, which reduce external fragmentation but causing internal fragmentation
> 

### Worst-fit:
(partitions) F = [100, 170, 40, 205, 300, 185]
(processes) P = [200, 15 , 185, 75, 175, 80]

- P[0] = 200 --> F[4] = 300 - 200 = 100
update:
Fs = [100, 170, 40, 205, 100, 185]

- P[1] = 15 --> F[3] = 205 - 15 = 190
update:
Fs = [100, 170, 40, 190, 100, 185]

- P[2] = 185 --> F[3] = 190 - 185 = 5
update:
Fs = [100, 170, 40, 5, 100, 185]

- P[3] = 75 --> F[5] = 185 - 75 = 110
update:
Fs = [100, 170, 40, 5, 100, 110]

- P[4] = 175 --> No space available
- P[5] = 80 --> F[1] = 170 - 80 = 90

> Worst fit may leave larger unusable memory partitions for future allocation, reducing external fragmentation but it also can cause internal fragmentation 


## Q3
### Mirroring / Shadowing - RAID 1
- Keeps duplicate of each disk

![](Pasted%20image%2020231209000337.png)

### Stripping - RAID 0
- Using a group of disks as one storage unit (split data)
- No redundancy, fault tolerance or parity. 
![](Pasted%20image%2020231209000204.png)

### Parity RAID 2,3,4,5,6,10
- also referred to as a checksum. Parity is a calculated value used to mathematically rebuild data
- Uses less redundancy 
![](Pasted%20image%2020231209000914.png)
![](Pasted%20image%2020231209000934.png)


## RAID
### RAID 0 --> striping
![](Pasted%20image%2020231209001341.png)
### RAID 1 --> Mirroring 
![](Pasted%20image%2020231209001354.png)
### RAID 3 --> Bit level Striping with hamming parity 
![](Pasted%20image%2020231209001926.png)
### RAID 3 --> Bit level Striping with dedicated parity 
![](Pasted%20image%2020231209001829.png)
### RAID 4 --> Block level Striping with parity 
![](Pasted%20image%2020231209001754.png)
### RAID 5 --> Striping with parity  
![](Pasted%20image%2020231209001714.png)
### RAID 6 --> Striping with double parity  
![](Pasted%20image%2020231209001654.png)
### RAID 10 (1+0) --> combining mirroring and striping 
![](Pasted%20image%2020231209001627.png)

>[source](https://phoenixnap.com/kb/raid-levels-and-types)