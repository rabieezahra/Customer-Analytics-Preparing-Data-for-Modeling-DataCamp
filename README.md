# Customer Analytics: Preparing Data for Modeling

## Overview

This project is part of a customer analytics workflow for **Training Data Ltd.**, an online data science training provider. The goal is to clean and optimize a large customer dataset so it can be used efficiently to predict whether students are looking for a new job.

The optimized dataset will help the company direct students to prospective recruiters.

## Business Problem

Large datasets can make model training and prediction slow. By storing the dataset with efficient data types, we can reduce memory usage and improve processing times without reducing the number of records.

## Dataset

The dataset `customer_train.csv` contains anonymized student information:

| Column | Description |
|---|---|
| `student_id` | A unique ID for each student |
| `city` | A code for the city the student lives in |
| `city_development_index` | A scaled development index for the city |
| `gender` | The student's gender |
| `relevant_experience` | Whether the student has relevant work experience |
| `enrolled_university` | Type of university course enrolled in, if any |
| `education_level` | The student's education level |
| `major_discipline` | The educational discipline of the student |
| `experience` | Total work experience in years |
| `company_size` | Number of employees at the student's current employer |
| `company_type` | Type of company employing the student |
| `last_new_job` | Years between current and previous jobs |
| `training_hours` | Number of training hours completed |
| `job_change` | Target variable: `1` if looking for a new job, `0` otherwise |

## Objectives

1. Convert binary categorical columns to `bool`.
2. Convert integer-only columns to `int32`.
3. Convert float columns to `float16`.
4. Convert nominal categorical columns to `category`.
5. Convert ordinal categorical columns to ordered `category`, preserving natural order.
6. Filter to students with 10 or more years of experience at companies with at least 1000 employees.
7. Reduce memory usage substantially.

## Approach

- Loaded the dataset with pandas.
- Mapped binary columns (`relevant_experience`, `job_change`) to Boolean values.
- Downcast integer columns (`student_id`, `training_hours`) to `int32`.
- Downcast float column (`city_development_index`) to `float16`.
- Converted nominal columns (`city`, `gender`, `major_discipline`, `company_type`) to `category`.
- Converted ordinal columns (`education_level`, `experience`, `company_size`, `last_new_job`, `enrolled_university`) to ordered categories.
- Filtered the dataset using ordered category comparisons.
- Validated dtypes, shape, and memory usage.

## Results

- Original shape: `(19158, 14)`
- Transformed shape: `(2201, 14)`
- Memory usage is significantly lower after dtype optimization.
- The transformed DataFrame is ready for modeling.
