# Discrete Loading Simulation for Fiber Survival Fraction and Avalanche Size

This section of the repository details the procedure for calculating the simulation data for the surviving fraction of fibers (U) and sub-avalanche size under discrete loading conditions.

## Main Simulation Code: `discrete_simulation.c`

### Inputs

- **Threshold Distribution**: Adjust the threshold distribution as needed.
- **System Size**: Specify the size of the system.

### Execution

Execute the `discrete_simulation.c` file to generate the required output files.

### Outputs

The simulation produces two output files:

#### 1. Surviving Fraction of Fiber (U)

**Output File**: `L=100000_time_simulation_U_0.01.txt`

**Columns**:
1. **Cumulative Sub-Avalanche Time**: Cumulative time of sub-avalanches.
2. **Sub-Avalanche Time for Specific Avalanche**: Time of specific sub-avalanches.
3. **Surviving Fraction of Fiber (U)**: The fraction of fibers that survive.

#### 2. Sub-Avalanche Size

**Output File**: `L=100000_time_simulation_S_0.01.txt`

**Columns**:
1. **Cumulative Sub-Avalanche Time**: Cumulative time of sub-avalanches.
2. **Sub-Avalanche Time for Specific Avalanche**: Time of specific sub-avalanches.
3. **Sub-Avalanche Size**: The size of specific sub-avalanches.

## Calculation of Limiting Time for Surviving Fraction of Fiber (U)

### Prerequisite

This step requires the completion of the `discrete_simulation.c` execution.

### Main Calculation Code: `cyclic_loading_u.c`

### Execution

Run the `cyclic_loading_u.c` file. This will produce the `time_U_0.01_new.txt` file.

### Output File: `time_U_0.01_new.txt`

**Columns**:
1. **Sub-Avalanche Time**: Time of specific sub-avalanches.
2. **Cumulative Sub-Avalanche Time**: Cumulative time of sub-avalanches.
3. **Surviving Fraction of Fiber**: The fraction of fibers that survive.

### Further Processing

Process the `time_U_0.01_new.txt` file using the `theoretical_align_U_simulation.c` script to obtain limited values of time and surviving fractions of fibers.

**Final Output File**: `time_U_0.01_trunc.txt`

## Additional Information

### Single Loading Condition

With minor modifications to the `cyclic_loading.c` code, it is possible to generate data for a single loading condition to calculate the surviving fraction of fibers.

### Numerical Calculation of Sub-Avalanche Size

To numerically calculate the sub-avalanche size and its corresponding time, use the data from `time_U_0.01_trunc.txt`. By differentiating the surviving fraction of fibers (U) and choosing the time difference to be approximately 1, the sub-avalanche size can be determined.

## How to Use

1. **Run Discrete Simulation**:
    - Modify the threshold distribution and system size as needed.
    - Compile and execute `discrete_simulation.c` to generate the required output files.

2. **Calculate Limiting Time**:
    - After running `discrete_simulation.c`, execute `cyclic_loading_u.c` to generate `time_U_0.01_new.txt`.

3. **Further Process Data**:
    - Use `theoretical_align_U_simulation.c` to process `time_U_0.01_new.txt` and generate `time_U_0.01_trunc.txt`.

## Conclusion

This documentation provides an overview of the codes and procedures for simulating the surviving fraction of fibers and sub-avalanche sizes under discrete loading conditions. By following the outlined steps, you can generate and process the necessary data for your research.
