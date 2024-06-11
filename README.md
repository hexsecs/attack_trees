# attack_trees


### Formula for Calculating Attack Trees Based on the EVITA Method

The EVITA (E-safety Vehicle Intrusion proTected Applications) method involves assessing the security of automotive systems by using attack trees. Attack trees are a formal method for modeling potential security threats. Here's an overview of the steps and formulas used in calculating attack trees based on the EVITA method:

#### **1. Attack Tree Structure**

An attack tree models how a system can be attacked. The tree consists of:
- **Nodes:** Each node represents a possible attack or a step in an attack.
- **Edges:** The connections between nodes represent the progression of the attack.

#### **2. Probability Calculation**

To calculate the probability of an attack using the EVITA method:

- **Leaf Node Probability:** For each leaf node, determine the probability \( P_i \) of the attack step occurring. This might be based on historical data, expert judgment, or probabilistic models.

- **AND Nodes:** For a parent node \( P_{AND} \) with \( n \) child nodes, the probability of the AND node occurring is the product of the probabilities of its child nodes.
  \[
  P_{AND} = \prod_{i=1}^{n} P_i
  \]

- **OR Nodes:** For a parent node \( P_{OR} \) with \( n \) child nodes, the probability of the OR node occurring is the probability that at least one of the child nodes occurs.
  \[
  P_{OR} = 1 - \prod_{i=1}^{n} (1 - P_i)
  \]

#### **3. Cost Calculation**

The cost associated with mitigating or dealing with an attack can also be assessed:
- **Leaf Node Cost:** Assign a cost \( C_i \) to each leaf node, representing the cost of mitigating or handling that attack step.

- **AND Nodes:** For a parent node \( C_{AND} \) with \( n \) child nodes, the cost is typically the sum of the costs of its child nodes.
  \[
  C_{AND} = \sum_{i=1}^{n} C_i
  \]

- **OR Nodes:** For a parent node \( C_{OR} \) with \( n \) child nodes, the cost might be the minimum cost among its child nodes, assuming that mitigating one child node may be sufficient.
  \[
  C_{OR} = \min_{i=1}^{n} C_i
  \]

#### **4. Impact Assessment**

Impact is assessed similarly:
- **Leaf Node Impact:** Assign an impact \( I_i \) to each leaf node, representing the potential impact if that attack step is successful.

- **AND Nodes:** For a parent node \( I_{AND} \) with \( n \) child nodes, the impact might be the sum of the impacts of its child nodes.
  \[
  I_{AND} = \sum_{i=1}^{n} I_i
  \]

- **OR Nodes:** For a parent node \( I_{OR} \) with \( n \) child nodes, the impact might be the maximum impact among its child nodes, assuming that any single child node's impact is significant.
  \[
  I_{OR} = \max_{i=1}^{n} I_i
  \]

### Steps for Applying the EVITA Method

1. **Model the Attack Tree:** Define the structure of your attack tree, including the nodes and their relationships.

2. **Assign Probabilities, Costs, and Impacts:** Determine the probabilities, costs, and impacts for each leaf node.

3. **Calculate Node Values:** Use the formulas above to calculate the probabilities, costs, and impacts for AND and OR nodes.

4. **Analyze Results:** Use the calculated values to assess the overall security posture of the system, focusing on the most significant threats based on their probability, cost, and impact.

### Example

Consider a simplified attack tree with two leaf nodes under an OR node:

- Leaf Node 1: \( P_1 = 0.2 \), \( C_1 = 100 \), \( I_1 = 50 \)
- Leaf Node 2: \( P_2 = 0.1 \), \( C_2 = 200 \), \( I_2 = 80 \)

For the OR node:
\[
P_{OR} = 1 - (1 - 0.2) \cdot (1 - 0.1) = 1 - 0.8 \cdot 0.9 = 1 - 0.72 = 0.28
\]
\[
C_{OR} = \min(100, 200) = 100
\]
\[
I_{OR} = \max(50, 80) = 80
\]

The probability of the OR node occurring is 0.28, with a cost of 100 and an impact of 80.

### References and Further Reading

- **EVITA Project Documentation**: [EVITA Project](https://www.evita-project.org/)
- **Schneier, Bruce. "Attack Trees: Modeling security threats."**
- **Jürjens, Jan. "Secure Systems Development with UML."**
