
# Experiment 2

## Design of 4-bit Ripple Carry Adder and Analysis of Propagation Delay

---

##  Objective

The objective of this experiment is to design and simulate a **4-bit Ripple Carry Adder (RCA)** using basic logic gates in Logisim Evolution and to analyze the propagation delay associated with carry generation and output computation. The experiment aims to understand how carry propagates through multiple full adders and how it affects the overall speed of the circuit.

---

## Background Study

A Ripple Carry Adder is a combinational circuit used to perform binary addition of multi-bit numbers. It is constructed by cascading multiple full adders, where the carry output of one stage becomes the carry input of the next stage. In a 4-bit Ripple Carry Adder, four full adders are connected in series to add two 4-bit binary numbers along with an initial carry input.

Each full adder computes a sum and a carry based on its inputs. However, the major drawback of this design is the propagation delay caused by the sequential flow of carry from the least significant bit (LSB) to the most significant bit (MSB). The final output is only obtained after the carry has propagated through all stages, making the circuit slower for larger bit sizes.

---

## Circuit Description

In this experiment, a 4-bit Ripple Carry Adder was implemented using basic logic gates such as AND, OR, and XOR. Each stage of the circuit represents a full adder, where two input bits and a carry input are processed to generate a sum and carry output. The carry output of each stage is connected to the next stage, forming a chain-like structure.

The circuit was simulated using Logisim, where different combinations of binary inputs were applied to verify the correctness of the sum and carry outputs. The propagation of carry through each stage was observed, highlighting the delay in obtaining the final result.

---

##  Circuit Diagram


[Lab Implentation(Logisim) of Experiment](https://github.com/241210047/241210047_COA/blob/main/Experiment_02/Lab_02.png)


---

## 🔍 Observations

The simulation showed that the sum outputs were generated correctly for all input combinations. However, it was observed that the carry signal propagates sequentially from one stage to another, introducing a delay in the final output. The delay increases with the number of bits, as each stage must wait for the carry from the previous stage before producing its result.

---

## ⏱️ Propagation Delay Analysis

The total propagation delay of a Ripple Carry Adder is directly proportional to the number of bits. In a 4-bit RCA, the worst-case delay occurs when the carry must propagate through all four stages. This delay can be expressed as the sum of delays of individual full adders, making the circuit slower compared to more advanced adders like carry look-ahead adders.

---

## 🎯 Result

The 4-bit Ripple Carry Adder was successfully designed and simulated using Logisim Evolution. The outputs were verified and found to be correct. The experiment clearly demonstrated the concept of carry propagation and highlighted the impact of propagation delay on circuit performance.

---

## 📚 Conclusion

This experiment provided a clear understanding of how multi-bit addition is performed using Ripple Carry Adders and how carry propagation affects the speed of computation. It emphasized the limitations of RCA in terms of delay and the need for more efficient adder designs in high-speed systems.

