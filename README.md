# Step-by-Step Explanation of the Project:

### Introduction to the Problem:

Start by explaining the problem statement: detecting structural faults in manufactured chips before delivery.
Mention that the task is to design an algorithm to identify the input vector required to detect a fault at a specific node in a circuit.

### Understanding the Inputs and Outputs:

Inputs: A circuit file, fault node location, and fault type (SA0 or SA1).
Outputs: An input vector to test the fault and the expected output value to confirm the fault, written to an output file.

### Circuit Representation:

The circuit is represented using a dictionary (unordered_map) where the key is the node, and the value is the logic expression associated with that node.
The parseCircuitFile function reads the circuit file and populates this dictionary.

### Generating Input Vectors:

The generate function creates all possible combinations of the four inputs (A, B, C, D), resulting in 16 different input vectors (2^4).

### Evaluating Logic Expressions:

The evalExpression function evaluates the logic expression for a given node using recursion.
It handles different logic gates (AND, OR, NOT, XOR) and resolves their values based on the input vector.
If the node is a basic input (A, B, C, D), it directly returns the corresponding value from the input vector.

### Circuit Evaluation:

The evalCircuit function uses the evalExpression function to compute the output of the circuit (Z) for a given input vector.

### Handling Faults:

A fault is introduced in the circuit by modifying the logic expression of the fault node to either "0" (SA0) or "1" (SA1).
This is done by creating a copy of the circuit (faultyCircuit) and altering the fault node's value.

### Simulating and Comparing Outputs:

The program iterates through all generated input vectors.
It computes the expected output of the fault-free circuit and the actual output of the faulty circuit for each input vector.
If a discrepancy is found between the expected and actual outputs, it identifies the input vector as a potential test vector.

### Outputting Results:

If a suitable input vector is found, it is written to the output file along with the faulty output.
If no discrepancies are found, indicating the fault is ATPG (Automatic Test Pattern Generation) untestable, it writes a message to the output file stating this.

### Execution Flow:

The main function handles user inputs for the fault node and fault type.
It parses the circuit file, generates input vectors, introduces the fault, simulates the circuit for each input vector, and writes the results to the output file.

### Key Functions Overview:

parseCircuitFile: Parses the circuit file and builds the circuit representation.
generate: Generates all possible input vectors.
evalExpression: Evaluates the logic expression for a given node.
evalCircuit: Evaluates the entire circuit for a given input vector.
printToOutput: Writes the test vector and expected output to the output file.

# Detailed Code Walkthrough:
### parseCircuitFile Function:

Opens the circuit file and reads it line by line.
Splits each line into a node and its logic expression and stores them in the circuit dictionary.

### generate Function:

Creates a vector of vectors representing all possible input combinations (0000 to 1111).

### evalExpression Function:

Recursively evaluates the logic expression for a node.
Handles different types of gates and the base cases for input nodes.

### evalCircuit Function:

Uses evalExpression to compute the output Z for the entire circuit based on the input vector.

### printToOutput Function:

Formats the input vector and output value into a readable format and writes it to the output file.

### main Function:

Manages the overall flow, including user input, fault introduction, circuit simulation, and result output.
