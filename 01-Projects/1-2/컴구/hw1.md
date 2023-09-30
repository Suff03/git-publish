**COSE222: Computer Architecture**

**Assignment #1**

**Due: Oct 6, 2023 (Friday) 11:59pm on Blackboard**

**Solutions (total points: 104)**

Please answer the following questions. Write your student ID and name on the top of the document.

Submit your homework with “**PDF**” format only. You can easily generate the pdf files from Microsoft Word or Hangul Word Processor (HWP). You can also handwrite your answers to scan the handwritten documents with “**PDF**” format. You can use document capture applications such as “Microsoft Lens” for scanning your documents with your smartphones.

The answer rules:

(1)  You can write answers in both Korean and English.

(2)  Please make your final answer numbers have two decimal places.

(3)  Performance of A is improved by _NN_ % compared to performance B if PerfA / PerfB = 1._NN_.

1. Write the definitions of the following terminologies. [Total 12 pts]

(a) Moore’s Law [4]

회로의 집적하는 트랜지스터의 개수가 2년마다 두 배로 증가한다는 법칙

(b)  Dennard Scaling [4]

 트랜지스터의 크가가 꾸준히 작아지고 이에 가하는 전압도 줄어들지만, 트랜지스터의 Frequency와 면적 당 개수(밀도)도 증가해 최종적으로 Power의 밀도는 꾸준히 유지된다.

(c)  Abstraction [4]

 중요하지 않은 세부적인 사항을 보이지 않게 하는 것. 추상화 덕분에 사용자는 컴퓨터의 내부 구조를 알지 못해도 원활히 컴퓨터를 이용할 수 있다.

2.  Write the eight great ideas in computer architecture research mentioned during the class. [8]

* Design for Moore’s Law

* Use abstraction to simplify design

* Make the common case fast

* Performance via parallelism

* Performance via pipelining

* Performance via prediction

* Hierarchy of memories

* Dependability via redundancy (for reliability)

3. Describe the steps that transform a program written in high-level language such as C into a representation that is **directly** executed by a computer processor. [4]

 C를 비롯한 컴파일 언어는 컴파일러에 의한 컴파일 과정에서 Assembly language로 변환된다. Assembly language는 어셈블러에 의해 0과 1로 이루어진 Machine Code로 변환된다.

4. Discuss why commodity CPU venders (such as Intel and AMD) do not manufacture single-core processors running with a very high clock frequency. Justify your answer. [4]

 전력 한계, 명령어 병렬화, 긴 메모리 지속 시간은 uniprocessor의 발전을 둔화시켰다. 제조사들은 멀티 프로세서 등의 방법으로 이 문제를 해결하고 있다.

5.  Computer A can execute a C program 10 times in one second and Computer B can execute the same C program 30 times in one second. If the MIPS (million instructions per second) rate of Computer A is MIPS_A and MIPS rate of Computer B is MIPS_B, then an engineer concludes that MIPS_B = MIPS_A x 3.
Under what conditions is this calculation correct? [4]

 동일한 ISA를 사용하고 동일한 프로그램을 실행해야 한다.

6.  **Student Y** stated that the performance of the ARM processor using 2 GHz clock exhibits higher performance than the x86 Pentium processor that runs with 1.5 GHz clock. Explain why the statement by **Student Y** is not always true. Please take a counter example in your answer. [4]

7.  Consider three different processors P1, P2, and P3 executing the same instruction set. P1 has 2.4GHz clock rate and a CPI of 1.2. P2 has a 3.0GHz clock rate and CPI of 1.4. P3 has a 4.0GHz clock rate and has a CPI of 2.2. [Total 12 pts]

(a)  Which processor has the highest performance expressed in **instructions per second**? [6]

**Sol)** IPS를 알기 위해 다음과 같은 식을 변형한다. $$\text{IPS}=\frac{\text{IC}}{\text{CPU Time}}=\frac{\text{Clock Rate}}{\text{CPI}}$$
$P_1=\frac{2.4}{1.2}, P_2=\frac{3.0}{1.4}, P_3=\frac{4.0}{2.2}$ (비율을 보기 위해 $GHz$ 생략)
IPS가 클수록 성능이 좋다고 볼 수 있다. 따라서, 답은 $P_2$.

(b) If the processors each execute a program in 10 seconds, find the **number of cycles** and the **number of instructions**. [6]

**Sol)**
CPU Time에 대한 공식
$$\text{CPU Time}=\text{Clock Cycles}\times \text{C}_t$$
을 변형하면,
$$\text{Clock Cycles}=\text{Clock Rate}\times \text{CPU Time}$$
을 얻을 수 있다.

Number of Cycles
${P_{1})} 10\times 2.4\times 10^{9}, {P_{2})} 10\times 3.0\times 10^{9},{P_{3})} 10\times 4.0\times 10^9$

Number of Instructions (IC)
Clock Cycles에 관한 식을 변형하면,
$$\frac{\text{Clock Cycles}}{\text{CPI}}=\text{IC}$$
${P_{1})} \frac{2.4\times 10^{10}}{1.2}, {P_{2})} \frac{3.0\times 10^{10}}{1.4},{P_{3})} \frac{4.0\times 10^{10}}{2.2}$

8. Consider the following processors P1 and P2. Note that P1 and P2 have different ISAs, thus the total number of instructions is different even if the application is written in the same high-level programming language. [Total 12 pts]

|   |   |   |   |
|---|---|---|---|
|Processor|Clock frequency|CPI|Instruction count|
|P1|3 GHz|2.5|3x10^9|
|P2|2 GHz|1.2|5x10^9|

(a)  Find the execution time of each processor. Which processor exhibits the better performance? [4]

**Sol)**
$$\frac{P_1}{P_2}=\frac{E_2}{E_1}=\frac{\frac{1.2\times5\times10^9}{2\times10^9}}{\frac{2.5\times3\times10^9}{3\times10^9}}=\frac{3}{2.5}>1$$
따라서, $P_1$이 성능이 더 좋다.

(b) We may use MIPS (_millions of instructions per second_) to compare the performance of two different processors. Calculate MIPS for processors P1 and P2. Which processor has better performance only considering MIPS? [4]

**Sol)**
$$\text{MIPS}=\frac{\text{IC}}{T\times10^6}$$ $${P_1})\frac{3\times10^{9}}{2.5\times10^6},{P_2})\frac{5\times10^9}{3
\times10^6}$$
(c)  Please explain why we cannot use MIPS directly to compare the performance of processors. [4]

**Sol)**
ISA, Program을 고려해야 함.

9. Let us assume that an application A is compiled to the different binary files B_aarch64 (for ARM ISA) and B_rv64 (for RISC-V ISA). We will run the compiled binaries on two different processors P1 (ARM processor) and P2 (RISC-V processor) respectively. The composition of instruction counts observed in these two binaries are shown in the below table. [Total 16 pts]

|   |   |   |   |   |
|---|---|---|---|---|
|Binaries|INT instruction|FP instruction|Mem instructions|Branch insts|
|B_aarch64|8x10^9|8x10^9|2x10^9|2x10^9|
|B_rv64|6x10^9|8x10^9|5x10^9|1x10^9|

The below table lists the CPIs by instruction types and the clock frequencies of processors P1 and P2.

|   |   |   |   |   |   |
|---|---|---|---|---|---|
|Processor|INT CPI|FP CPI|Mem CPI|Branch CPI|Clock freq.|
|P1 (ARM)|1|10|6|4|2.0 GHz|
|P2 (RISC-V)|1|8|4|9|1.5 GHz|

(a)  Compute the average CPIs of the processors P1 and P2 respectively. [6]

(b) Can we use the CPIs calculated above for comparing the performance of the processors P1 and P2 in this case? Why? [4]

(c)  Compare the performance of the above processors P1 and P2. You should notify _which processor_ _exhibits better performance by ##.# %_ in your answer. [6]

10. Consider two different implementations of **the same instruction set architecture**. The instructions can be divided into four classes according to their CPI (classes A, B, C, and D). Consider the following two processors and an application. [Total 16 pts]

**P1: Clock frequency = 2.0GHz, CPIs for each instruction class = 1, 2, 3, 3**

**P2: Clock frequency = 3.0GHz, CPIs for each instruction class = 2, 2, 2, 2**

**Application:** 

**Instruction count = 1.0x106,** 

**fractions by instruction classes: class A = 20%, class B = 10%, class C = 40%, class D = 30%** (a) Which processor is faster: P1 or P2? [6]

(b)  What is the global CPI for each implementation? [6]

(c)  Figure out the clock cycles required in both cases. [4]

11. Assume a program requires the execution of 50x106 FP instructions, 110x106 INT instructions,

80x106 load/store instructions, and 16x106 branch instructions. The CPI for each type of instruction

(FP, INT, load/store, and branch types) is 1, 1, 4, and 2, respectively. Assume that the processor has a 2GHz clock rate. [Total 12 pts]

(a)               By how much must we improve the CPI of FP instructions if we want the program to run two times faster? [6]

(b)               By how much is the execution time of the program improved if the CPI of INT and FP instructions is reduced by 40% and the CPI of load/store and branch instructions is reduced by 30%? [6]