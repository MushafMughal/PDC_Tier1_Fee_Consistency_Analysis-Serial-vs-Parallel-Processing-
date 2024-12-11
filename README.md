# Fee Consistency Analysis: Serial vs Parallel Processing
This project demonstrates the analysis of fee submission data to calculate the most consistent payment day for each student. It compares two computational approaches: Serial and Parallel Processing, and measures their performance improvement.

## Overview
The project compares the Serial and Parallel processing approaches to determine the efficiency of parallel computing in data processing tasks using Python.

By utilizing pandas for data manipulation and multiprocessing for parallelization, we measure the time taken by each approach to compute the desired result.

## Dataset Description
Two datasets are used:

1. **larger_fees.csv**:
    - Columns: ['student_id', 'fee_submission_date', 'day_of_month']
    - Contains fee submission records, including the specific day of the month the fees were submitted.
2. **larger_students.csv**:
    - Columns: ['student_id', 'name', 'department', 'semester']
    - Contains student details such as name, department, and semester.

## Objectives
1. **Create a new DataFrame**:
    - Columns: ['student_id', 'name', 'department', 'semester', 'Most Consistent Payment Day']
    - The column Most Consistent Payment Day is calculated as the mode of day_of_month (most frequent day fees are paid) for each student_id.
      
2. **Compare Serial and Parallel Processing**:
    - Serial Approach: Process data sequentially.
    - Parallel Approach: Utilize multiprocessing for faster computation.
      
3. Measure and report performance improvements.

## Implementation
### Serial Approach
 - Group df1 by student_id using .groupby() and calculate the most frequent payment day (mode).
 - Merge the result with df2 on student_id to enrich the dataset.
### Parallel Approach
 - Split df1 into chunks grouped by student_id.
 - Use multiprocessing.Pool to compute the most frequent payment day for each group in parallel.
 - Combine the results and merge with df2.
### Performance Measurement
 - Use time.time() to measure execution time for both approaches.
 - Calculate the percentage improvement of Parallel Processing over Serial Processing.

## Results
### Example Output
   ![image](https://github.com/user-attachments/assets/acde7c71-fb02-4339-9a65-ade7824c2131)
### Performance Comparison
 - The performance improvement in this case:

   **serial_duration** = 0.0906, **parallel_duration** = 0.0709

   percent_faster = ( (serial_duration - parallel_duration) / serial_duration ) * 100
   
- Parallel Processing is **21.74%** faster than Serial Processing in my case.

## Future Improvements
 - Add error handling for missing or incomplete datasets.
 - Test on larger datasets to evaluate scalability.
 - Explore GPU acceleration using libraries like RAPIDS or Dask.
