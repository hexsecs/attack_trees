## Calculating Attack Trees Using the EVITA Method

The EVITA (E-safety Vehicle Intrusion proTected Applications) method involves assessing the security of automotive systems by using attack trees. Attack trees are a formal method for modeling potential security threats. Below is a guide on how to calculate attack trees based on the EVITA method.

The attack feasibility rating in the context of the EVITA methodology and ISO/SAE 21434 standards is calculated based on multiple factors that assess the difficulty of executing an attack. 

The factors include:
1. **Elapsed Time (ET)**: How long the attack takes to execute.
2. **Specialist Expertise (E)**: The level of expertise required to carry out the attack.
3. **Knowledge (K)**: The level of knowledge required about the system or the attack.
4. **Window of Opportunity (WO)**: The duration and difficulty of the opportunity window to perform the attack.
5. **Equipment (EQ)**: The type of equipment required to perform the attack.

### **Calculating the Attack Potential**

#### **1. Elapsed Time (ET)**

- **0**: < 1 day
- **1**: ≤ 1 week
- **4**: ≤ 1 month
- **10**: ≤ 3 months
- **17**: ≤ 6 months
- **19**: > 6 months

#### **2. Specialist Expertise (E)**

- **0**: Layman
- **3**: Proficient
- **6**: Expert
- **8**: Multiple Experts

#### **3. Knowledge (K)**

- **0**: Public
- **3**: Restricted
- **7**: Confidential
- **11**: Strictly Confidential

#### **4. Window of Opportunity (WO)**

- **0**: Unlimited
- **1**: Easy
- **4**: Moderate
- **10**: Difficult

#### **5. Equipment (EQ)**

- **0**: Standard
- **4**: Specialized
- **7**: Bespoke
- **9**: Multiple Bespoke

### **Steps to Calculate Attack Feasibility Rating**

1. **Assess Each Factor**:
   - Each factor is assigned a score according to the values defined above.

2. **Sum the Scores**:
   - The individual scores for ET, E, K, WO, and EQ are summed to produce a total attack potential score.

3. **Determine the Feasibility Level**:
   - The summed score can be mapped to an attack feasibility level, where lower scores indicate higher feasibility (easier attack) and higher scores indicate lower feasibility (more difficult attack).

#### **Example Calculation**

Suppose we have the following scores for a particular attack step:

- **Elapsed Time (ET)**: **4** (≤ 1 month)
- **Specialist Expertise (E)**: **6** (Expert)
- **Knowledge (K)**: **7** (Confidential)
- **Window of Opportunity (WO)**: **4** (Moderate)
- **Equipment (EQ)**: **4** (Specialized)

The total score would be:

`{Total Attack Potential} = 4 + 6 + 7 + 4 + 4 = 25`

The higher the total score, the less feasible the attack is. Conversely, a lower total score indicates a more feasible (easier) attack.


### 1. Attack Tree Structure

An attack tree models how a system can be attacked. The tree consists of:
- **Nodes**: Each node represents a possible attack or a step in an attack.
- **Edges**: The connections between nodes represent the progression of the attack.

### 2. Probability Calculation

To calculate the probability of an attack using the EVITA method:

- **Leaf Node Probability**: For each leaf node, determine the probability `P_i` of the attack step occurring. This might be based on historical data, expert judgment, or probabilistic models.

- **AND Nodes**: For a parent node `P_{\text{AND}}` with `n` child nodes, the probability of the AND node occurring is the product of the probabilities of its child nodes.

$$
P_{\text{AND}} = \prod_{i=1}^{n} P_i
$$

- **OR Nodes**: For a parent node \( P_{\text{OR}} \) with \( n \) child nodes, the probability of the OR node occurring is the probability that at least one of the child nodes occurs.

$$
P_{\text{OR}} = 1 - \prod_{i=1}^{n} (1 - P_i)
$$

### 3. Cost Calculation

The cost associated with mitigating or dealing with an attack can also be assessed:
- **Leaf Node Cost**: Assign a cost \( C_i \) to each leaf node, representing the cost of mitigating or handling that attack step.

- **AND Nodes**: For a parent node \( C_{\text{AND}} \) with \( n \) child nodes, the cost is typically the sum of the costs of its child nodes.

$$
C_{\text{AND}} = \sum_{i=1}^{n} C_i
$$

- **OR Nodes**: For a parent node \( C_{\text{OR}} \) with \( n \) child nodes, the cost might be the minimum cost among its child nodes, assuming that mitigating one child node may be sufficient.

$$
C_{\text{OR}} = \min_{i=1}^{n} C_i
$$

### 4. Impact Assessment

Impact is assessed similarly:
- **Leaf Node Impact**: Assign an impact \( I_i \) to each leaf node, representing the potential impact if that attack step is successful.

- **AND Nodes**: For a parent node \( I_{\text{AND}} \) with \( n \) child nodes, the impact might be the sum of the impacts of its child nodes.

$$
I_{\text{AND}} = \sum_{i=1}^{n} I_i
$$

- **OR Nodes**: For a parent node \( I_{\text{OR}} \) with \( n \) child nodes, the impact might be the maximum impact among its child nodes, assuming that any single child node's impact is significant.

$$
I_{\text{OR}} = \max_{i=1}^{n} I_i
$$

### Steps for Applying the EVITA Method

1. **Model the Attack Tree**: Define the structure of your attack tree, including the nodes and their relationships.
   
2. **Assign Probabilities, Costs, and Impacts**: Determine the probabilities, costs, and impacts for each leaf node.
   
3. **Calculate Node Values**: Use the formulas above to calculate the probabilities, costs, and impacts for AND and OR nodes.

4. **Analyze Results**: Use the calculated values to assess the overall security posture of the system, focusing on the most significant threats based on their probability, cost, and impact.

### Example

Consider a simplified attack tree with two leaf nodes under an OR node:

- Leaf Node 1: \( P_1 = 0.2 \), \( C_1 = 100 \), \( I_1 = 50 \)
- Leaf Node 2: \( P_2 = 0.1 \), \( C_2 = 200 \), \( I_2 = 80 \)

For the OR node:

$$
P_{\text{OR}} = 1 - (1 - 0.2) \cdot (1 - 0.1) = 1 - 0.8 \cdot 0.9 = 1 - 0.72 = 0.28
$$

$$
C_{\text{OR}} = \min(100, 200) = 100
$$

$$
I_{\text{OR}} = \max(50, 80) = 80
$$

The probability of the OR node occurring is 0.28, with a cost of 100 and an impact of 80.

### References and Further Reading

- **EVITA Project Documentation**: [EVITA Project](https://www.evita-project.org/)
- **Schneier, Bruce. "Attack Trees: Modeling security threats."**
- **Jürjens, Jan. "Secure Systems Development with UML."**
